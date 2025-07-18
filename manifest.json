<!-- index.html atualizado com suporte a PWA -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dúvidas sobre Produção Animal</title>
  <link rel="manifest" href="manifest.json">
  <meta name="theme-color" content="#0288d1">
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, sans-serif;
      background-color: #f0f8ff;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 720px;
      margin: 2rem auto;
      background: #fff;
      padding: 2rem;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    img.logo {
      display: block;
      max-width: 180px;
      margin: 0 auto 1rem;
    }
    h1 {
      text-align: center;
      color: #01579b;
      margin-bottom: 1.5rem;
    }
    input, select, button {
      width: 100%;
      padding: 0.9rem;
      margin: 0.5rem 0;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 1rem;
      box-sizing: border-box;
    }
    button {
      background-color: #0288d1;
      color: white;
      font-weight: bold;
      cursor: pointer;
      border: none;
    }
    button:hover {
      background-color: #0277bd;
    }
    .result {
      margin-top: 1.5rem;
      background: #f9f9f9;
      padding: 1rem;
      border-left: 4px solid #0288d1;
      border-radius: 6px;
    }
    a {
      color: #01579b;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="container">
    <img src="logo.png" alt="Logo do site" class="logo" />
    <h1>Dúvidas sobre Produção Animal</h1>
    <input type="text" id="duvida" placeholder="Digite sua dúvida..." />
    <select id="especie">
      <option value="">Todas as espécies</option>
      <option value="bovinos">Bovinos</option>
      <option value="suínos">Suínos</option>
      <option value="aves">Aves</option>
      <option value="ovinos">Ovinos</option>
      <option value="peixes">Peixes</option>
      <option value="abelhas">Abelhas</option>
      <option value="búfalos">Búfalos</option>
      <option value="rãs">Rãs</option>
      <option value="equinos">Equinos</option>
      <option value="coelhos">Coelhos</option>
    </select>
    <input type="number" id="ano" placeholder="Ano mínimo (ex: 2020)" />
    <button onclick="buscar()">Buscar Artigos</button>
    <div id="resultados"></div>
  </div>

  <script>
    function transformarDuvida(entrada) {
      let termos = entrada.toLowerCase();

      const palavrasChave = {
        "quanto tempo": "longevidade",
        "vive": "",
        "pirarucu": "pirarucu",
        "criar galpão": "ambiência instalações",
        "criação de aves": "avicultura",
        "alimentação": "nutrição animal",
        "engorda": "ganho de peso",
        "crescimento": "desenvolvimento animal"
      };

      for (let chave in palavrasChave) {
        if (termos.includes(chave)) {
          termos = termos.replace(chave, palavrasChave[chave]);
        }
      }

      return termos.trim();
    }

    function buscar() {
      const duvida = document.getElementById("duvida").value.trim();
      const especie = document.getElementById("especie").value.trim();
      const ano = document.getElementById("ano").value.trim();
      const resultados = document.getElementById("resultados");

      if (!duvida) {
        resultados.innerHTML = "<p style='color:red;'>Por favor, digite uma dúvida.</p>";
        return;
      }

      let duvidaConvertida = transformarDuvida(duvida);
      if (especie) duvidaConvertida += " " + especie;
      duvidaConvertida += " produção animal";
      if (ano) duvidaConvertida += " ano:" + ano;

      const termoBusca = encodeURIComponent(duvidaConvertida);

      resultados.innerHTML = `
        <div class="result">
          <strong>🔍 Google Scholar:</strong><br>
          <a href="https://scholar.google.com/scholar?q=${termoBusca}" target="_blank">Ver resultados</a>
        </div>
        <div class="result">
          <strong>📚 Scielo:</strong><br>
          <a href="https://search.scielo.org/?q=${termoBusca}" target="_blank">Ver resultados</a>
        </div>
        <div class="result">
          <strong>🏛️ Repositório UNESP:</strong><br>
          <a href="https://repositorio.unesp.br/simple-search?query=${termoBusca}" target="_blank">Ver resultados</a>
        </div>
        <div class="result">
          <strong>👨‍💼 Pesquisadores no LinkedIn:</strong><br>
          <a href="https://www.linkedin.com/search/results/people/?keywords=${termoBusca}" target="_blank">Buscar profissionais</a>
        </div>
      `;
    }

    if ('serviceWorker' in navigator) {
      window.addEventListener('load', () => {
        navigator.serviceWorker.register('service-worker.js')
          .then(reg => console.log('Service Worker registrado'))
          .catch(err => console.error('Erro no Service Worker:', err));
      });
    }
  </script>
</body>
</html>


Pronto, Caio! Agora seu site é um PWA (Progressive Web App) — ou seja, pode ser instalado no celular como se fosse um app Android, direto do navegador! 📱


---

✅ Próximos arquivos que você precisa adicionar no repositório GitHub

1. manifest.json

Crie um novo arquivo com esse nome e esse conteúdo:

{
  "name": "Dúvidas sobre Produção Animal",
  "short_name": "Dúvidas Animal",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#f0f8ff",
  "theme_color": "#0288d1",
  "icons": [
    {
      "src": "logo.png",
      "type": "image/png",
      "sizes": "192x192"
    }
  ]
}

> Você pode usar o mesmo logo.png como ícone.




---

2. service-worker.js

Crie um arquivo chamado service-worker.js com o conteúdo básico abaixo (já habilita o modo PWA):

self.addEventListener('install', event => {
  console.log('Service Worker instalado');
  self.skipWaiting();
});

self.addEventListener('activate', event => {
  console.log('Service Worker ativado');
});

self.addEventListener('fetch', function(event) {
  event.respondWith(fetch(event.request));
});


---

✅ Como testar

1. Atualize os arquivos no GitHub


2. O Vercel vai automaticamente fazer o deploy


3. Acesse o site pelo celular (Android)


4. No navegador, deve aparecer a opção: "Adicionar à tela inicial"


5. Depois disso, ele funciona como um app nativo!




---

Se quiser, posso gerar os ícones automaticamente ou deixar ele compatível com a Play Store depois. Só me avisar! 🚀

