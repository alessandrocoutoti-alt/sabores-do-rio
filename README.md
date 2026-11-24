# Sabores do Rio: Cardápio Digital Interativo

Trabalho final da Unidade VI (Web Semântica e Tecnologias Multimodais), Grupo 6, Desenvolvimento de Sistemas, Centro Universitário Fametro.

Protótipo didático de cardápio digital feito só com **HTML5, CSS3 e JavaScript**, sem backend. Os dados vêm de **Microdados (Schema.org)** (Obj. 572) e o pedido é feito por **comandos de voz com a Web Speech API** (Obj. 573).

Site publicado: https://saboresdorio.vercel.app/

## Estrutura
- `index.html`: página, com os Microdados (Restaurant, Menu, MenuSection, MenuItem, Offer e PropertyValue)
- `css/style.css`: visual responsivo, foco visível, modo escuro e alto contraste
- `js/script.js`: leitura dos dados, filtros, busca, pedido, voz, temas, atalhos, validação dos dados e conversão para JSON-LD
- `img/`: fotos dos 13 pratos e a imagem de capa (geradas por IA)

## 1. Como iniciar o protótipo
Use o **Chrome ou o Edge** (a voz não funciona no Firefox).

- **Opção A, mais simples:** abra o `index.html` com duplo clique.
- **Opção B, servidor estático:** no VS Code, clique com o botão direito em `index.html` e escolha *Open with Live Server*. Ou, na pasta do projeto, rode `python -m http.server 8000` e abra `http://localhost:8000`.
- **Opção C:** acesse o link publicado acima.

Não precisa instalar nada nem ter banco de dados. Os dados são simulados.

## 2. Como testar a voz
1. Clique no botão do microfone (ou aperte `M`) e **permita o uso do microfone** quando o navegador pedir.
2. Fale um comando e veja a resposta na tela e em voz alta. Para desligar a resposta falada, desmarque "Responder em voz alta".
3. Se a voz não funcionar, digite o comando no campo "Ou digite um comando" e clique em Enviar.

Comandos de exemplo:
- `quero duas moquecas`, `adicionar um pastel`, `remover pastel`
- `sem glúten`, `sem castanhas`, `sem crustáceos`, `mostrar tudo`
- `o que tem sem lactose?`, `buscar cupuaçu`, `limpar busca`
- `mesa 5`, `observação sem cebola`, `qual o total`
- `mostrar pedido`, `finalizar pedido`

Se o cliente pedir um prato com um alérgeno que ele marcou, o sistema avisa antes de adicionar.

## 3. Como testar a acessibilidade
- **Teclado:** use `Tab` e `Shift+Tab` para navegar, `Enter` e `Espaço` para acionar. O foco aparece bem destacado. Há o link "Pular para o cardápio" no começo da página.
- **Atalhos:** `/` busca, `M` microfone, `P` abre o pedido, `D` modo escuro, `C` alto contraste (também listados na página, em "Atalhos de teclado").
- **Temas:** botões "Modo escuro" e "Alto contraste" no topo. O modo escuro acompanha a preferência do aparelho, e a escolha fica salva no navegador.
- **Leitor de tela (NVDA, VoiceOver ou TalkBack):** botões e grupos têm rótulos ARIA, a contagem de pratos e as respostas do sistema são anunciadas (aria-live), e emojis decorativos ficam ocultos.

## 4. Como inspecionar a camada semântica
Os dados dos pratos estão marcados no próprio HTML com Microdados do Schema.org.

1. **Botão na página:** clique em **"Ver dados semânticos (JSON-LD)"**. O painel mostra os Microdados convertidos em JSON-LD (13 pratos, com preço, alérgenos e dietas) e permite copiar o código.
2. **DevTools:** aperte `F12`, abra a aba *Elements* e procure por `itemscope`, `itemtype` e `itemprop` (por exemplo, dentro de cada `<article class="prato">`).
3. **Validador oficial:** cole o JSON-LD copiado em https://validator.schema.org (aba *Code Snippet*), ou informe o link do site publicado.
4. **Validação de dados no próprio código:** se algum prato estiver sem nome, preço ou palavras-chave de voz, a página mostra um aviso e escreve o problema no console (`F12`, aba *Console*).

Vocabulário usado: `Restaurant` › `Menu` › `MenuSection` › `MenuItem`, com `Offer` (preço), `PropertyValue` (alérgenos) e `suitableForDiet` (dietas).

## Como publicar na Vercel
1. Envie para a raiz do repositório no GitHub: `index.html` e as pastas `css`, `js` e `img`.
2. Conecte o repositório à Vercel. Cada novo commit na branch `main` publica o site de novo.
3. O arquivo precisa se chamar `index.html`, senão a Vercel mostra erro 404.

## Limitações conhecidas
- A voz usa a Web Speech API: funciona melhor no Chrome e no Edge, não funciona no Firefox e pode variar no Safari. Exige permissão de microfone e pode errar com ruído.
- O pedido não é enviado a nenhuma cozinha: a confirmação é simulada (sem backend, login ou pagamento).
- O pedido em andamento e o tema escolhido ficam salvos apenas no navegador do aparelho.
- As fotos são geradas por IA e ilustrativas; preços, pratos e alérgenos são fictícios.
- As fontes vêm do Google Fonts; sem internet, o site usa fontes do sistema.
- Os testes foram manuais e automáticos (html-validate, axe-core e extruct), sem certificação formal de acessibilidade.
