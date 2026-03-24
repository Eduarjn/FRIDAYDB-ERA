// ══════════════════════════════════════════════════════════════
//  Cloudflare Worker — Backend seguro para o Agente IPBX
//  Deploy: https://workers.cloudflare.com (plano gratuito)
// ══════════════════════════════════════════════════════════════
//
//  Variáveis de ambiente a configurar no painel da Cloudflare:
//    ANTHROPIC_API_KEY  →  sua chave da API do Claude
//    ACCESS_PASSWORD    →  senha opcional de acesso (pode deixar vazia)
//
// ══════════════════════════════════════════════════════════════

export default {
  async fetch(request, env) {

    // Libera CORS para qualquer origem (necessário para GitHub Pages)
    const corsHeaders = {
      'Access-Control-Allow-Origin': '*',
      'Access-Control-Allow-Methods': 'POST, OPTIONS',
      'Access-Control-Allow-Headers': 'Content-Type, X-Access-Password',
    };

    // Responde pre-flight OPTIONS
    if (request.method === 'OPTIONS') {
      return new Response(null, { status: 204, headers: corsHeaders });
    }

    if (request.method !== 'POST') {
      return new Response('Método não permitido', { status: 405, headers: corsHeaders });
    }

    // Verifica senha de acesso (se configurada)
    if (env.ACCESS_PASSWORD) {
      const senha = request.headers.get('X-Access-Password') || '';
      if (senha !== env.ACCESS_PASSWORD) {
        return new Response(JSON.stringify({ error: 'Senha incorreta' }), {
          status: 401,
          headers: { ...corsHeaders, 'Content-Type': 'application/json' }
        });
      }
    }

    // Lê o body enviado pela interface
    let body;
    try {
      body = await request.json();
    } catch {
      return new Response(JSON.stringify({ error: 'Body inválido' }), {
        status: 400,
        headers: { ...corsHeaders, 'Content-Type': 'application/json' }
      });
    }

    // Repassa para a API do Claude
    const claudeRes = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': env.ANTHROPIC_API_KEY,
        'anthropic-version': '2023-06-01',
      },
      body: JSON.stringify(body),
    });

    const data = await claudeRes.json();

    return new Response(JSON.stringify(data), {
      status: claudeRes.status,
      headers: { ...corsHeaders, 'Content-Type': 'application/json' }
    });
  }
};
