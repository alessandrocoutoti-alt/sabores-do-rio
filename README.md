# Sabores do Rio: Cardápio Digital Interativo

Projeto do Grupo 6 (Desenvolvimento de Sistemas, Centro Universitário Fametro).
Site estático feito só com HTML, CSS e JavaScript, sem backend.

## Estrutura
- `index.html`: página, com Microdados (schema.org) em Restaurant, Menu, MenuSection e MenuItem
- `img/`: fotos dos 13 pratos e imagem de capa (geradas por IA)
- `css/style.css`: visual, layout responsivo, foco visível e tema de alto contraste
- `js/script.js`: filtro de 7 alérgenos (glúten, lactose, ovo, peixe, castanhas, amendoim e crustáceos), busca, índice de seções, validação dos dados, atalhos, pedido, mesa, observação, comandos de voz e tema

## Como executar
Abra o `index.html` no Chrome ou no Edge (a voz não funciona em todos os navegadores).
Para publicar, envie esta pasta para um repositório no GitHub e conecte à Vercel.

## Comandos de voz
"quero duas moquecas", "remover pastel", "sem glúten", "mostrar tudo", "o que tem sem lactose?",
"buscar cupuaçu", "limpar busca", "mesa 5", "observação sem cebola", "qual o total", "mostrar pedido", "finalizar pedido".

## Acessibilidade
Atalhos de teclado (/, M, P, D, C), navegação por teclado, link "Pular para o cardápio", rótulos ARIA, ícones decorativos ocultos
modo escuro e botão de alto contraste. Testes manuais, sem certificação formal.

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
- Os testes foram manuais e automáticos, sem certificação formal de acessibilidade.
