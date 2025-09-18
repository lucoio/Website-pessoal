[README.txt](https://github.com/user-attachments/files/22412982/README.txt)
Website Pessoal - Luis Henrique

Um portfólio moderno e responsivo desenvolvido com HTML, CSS e JavaScript vanilla.

Como funciona o código

Este website é composto por 3 arquivos principais que trabalham juntos:

index.html - A Estrutura
O arquivo HTML funciona como o esqueleto do site, define o conteúdo e a estrutura.
O navegador lê este arquivo primeiro e usa as tags HTML para organizar o conteúdo.

style.css - A Aparência  
Define como o site vai ficar visualmente (cores, fontes, layout).
Conecta-se ao HTML através de classes como class="site-header".

script.js - A Interatividade
Adiciona comportamento dinâmico ao site.
Escuta eventos do usuário (cliques, scroll) e responde a eles.

Estrutura dos arquivos

Website Pessoal
├── Website_Pessoal_Luis_Henrique.html  (Estrutura do site)
├── Website_Pessoal_Luis_Henrique.css   (Estilos e aparência)
├── Website_Pessoal_Luis_Henrique.js    (Funcionalidades interativas)
└── README.txt                          (Este arquivo de explicação)

Explicação detalhada

HTML - A Base de Tudo

O arquivo HTML funciona como um documento estruturado:

<!DOCTYPE html>                    <!-- Diz ao navegador que é HTML5 -->
<html lang="pt-BR">                <!-- Idioma do site -->
<head>                             <!-- Informações invisíveis -->
  <meta charset="UTF-8">           <!-- Codificação de caracteres -->
  <title>Luis Henrique - Portfólio</title>  <!-- Título da aba -->
  <link rel="stylesheet" href="style.css">  <!-- Conecta o CSS -->
</head>
<body>                             <!-- Conteúdo visível -->
  <header class="site-header">     <!-- Cabeçalho com classe para CSS -->
    <h1>Luis Henrique</h1>         <!-- Título principal -->
    <nav class="main-nav">         <!-- Menu de navegação -->
      <a href="#inicio">Início</a> <!-- Links que apontam para seções -->
    </nav>
  </header>
  
  <main>                           <!-- Conteúdo principal -->
    <section id="inicio">          <!-- Seção com ID único -->
      <h2>Bem-vindo ao meu portfólio</h2>
    </section>
  </main>
</body>
</html>

Conceitos importantes:
- Tags: h1, p, div são como caixas que organizam o conteúdo
- Classes: class="site-header" permite que o CSS estilize elementos específicos
- IDs: id="inicio" cria identificadores únicos para navegação
- Links âncora: href="#inicio" faz o link apontar para uma seção específica

CSS - A Beleza Visual

O CSS funciona como um sistema de regras de estilo:

/* Reset básico - remove estilos padrão do navegador */
* {
  margin: 0;           /* Remove espaçamento externo */
  padding: 0;          /* Remove espaçamento interno */
  box-sizing: border-box;  /* Facilita cálculos de tamanho */
}

/* Estilizando o cabeçalho */
.site-header {
  background: #fff;              /* Fundo branco */
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);  /* Sombra sutil */
  padding: 1rem 0;              /* Espaçamento interno */
  position: sticky;             /* Fica grudado no topo */
  top: 0;                       /* Posição no topo */
  z-index: 100;                 /* Fica acima de outros elementos */
}

/* Estilizando links de navegação */
.main-nav a {
  color: #555;                  /* Cor do texto */
  text-decoration: none;        /* Remove sublinhado */
  padding: 0.5rem 1rem;         /* Espaçamento interno */
  border-radius: 4px;           /* Cantos arredondados */
  transition: all 0.3s;         /* Animação suave */
}

/* Efeito hover - quando o mouse passa por cima */
.main-nav a:hover {
  background: #e9ecef;          /* Muda o fundo */
  color: #2c3e50;               /* Muda a cor do texto */
}

Conceitos importantes:
- Seletores: .site-header seleciona elementos com essa classe
- Propriedades: background, color, padding definem características visuais
- Valores: #fff (branco), 1rem (unidade de medida), 4px (pixels)
- Pseudo-classes: :hover ativa estilos quando o mouse passa por cima

JavaScript - A Mágica Interativa

O JavaScript adiciona comportamento dinâmico:

// Aguarda o HTML carregar completamente
document.addEventListener('DOMContentLoaded', function() {
  
  // Seleciona todos os links de navegação
  const navLinks = document.querySelectorAll('.main-nav a');
  
  // Para cada link, adiciona um escutador de clique
  navLinks.forEach(link => {
    link.addEventListener('click', function(e) {
      e.preventDefault();  // Impede o comportamento padrão do link
      
      // Pega o ID da seção alvo (remove o #)
      const targetId = this.getAttribute('href').substring(1);
      const targetSection = document.getElementById(targetId);
      
      // Se a seção existe, rola suavemente até ela
      if (targetSection) {
        targetSection.scrollIntoView({
          behavior: 'smooth',  // Animação suave
          block: 'start'       // Alinha no topo
        });
      }
    });
  });
  
  // Escuta o scroll da página
  window.addEventListener('scroll', function() {
    const sections = document.querySelectorAll('section[id]');
    const scrollPos = window.scrollY + 100;  // Posição atual + offset
    
    // Para cada seção, verifica se está visível
    sections.forEach(section => {
      const sectionTop = section.offsetTop;
      const sectionHeight = section.offsetHeight;
      const sectionId = section.getAttribute('id');
      
      // Se a seção está na área visível
      if (scrollPos >= sectionTop && scrollPos < sectionTop + sectionHeight) {
        // Remove classe "active" de todos os links
        navLinks.forEach(link => {
          link.classList.remove('active');
          // Adiciona classe "active" ao link correspondente
          if (link.getAttribute('href') === '#' + sectionId) {
            link.classList.add('active');
          }
        });
      }
    });
  });
});

Conceitos importantes:
- Event Listeners: Escutam ações do usuário (cliques, scroll)
- DOM: Document Object Model - como o JavaScript vê o HTML
- Seletores: querySelectorAll() encontra elementos no HTML
- Animações: scrollIntoView() cria movimento suave
- Classes CSS: classList.add() adiciona estilos dinamicamente

Funcionalidades implementadas

Navegação Suave
Como funciona: JavaScript intercepta cliques nos links e rola suavemente até a seção
Código chave: scrollIntoView({ behavior: 'smooth' })

Link Ativo Dinâmico
Como funciona: JavaScript detecta qual seção está visível e destaca o link correspondente
Código chave: window.scrollY calcula posição do scroll

Design Responsivo
Como funciona: CSS usa media queries para adaptar o layout a diferentes tamanhos de tela
Benefício: Site funciona bem em celular, tablet e desktop

Efeitos Visuais
- Hover effects: Links mudam de cor quando o mouse passa por cima
- Sombras: Elementos têm sombras sutis para profundidade
- Transições: Mudanças são suaves, não abruptas

Como executar

Método 1: Abrir diretamente
1. Baixe todos os arquivos
2. Renomeie os arquivos para:
   - Website_Pessoal_Luis_Henrique.html → index.html
   - Website_Pessoal_Luis_Henrique.css → style.css
   - Website_Pessoal_Luis_Henrique.js → script.js
3. Clique duas vezes no index.html

Método 2: Servidor local (recomendado)
1. Instale uma extensão "Live Server" no VS Code
2. Clique com botão direito no index.html
3. Selecione "Open with Live Server"

Tecnologias utilizadas

HTML5 - Estrutura e semântica do conteúdo
CSS3 - Estilização e layout responsivo
JavaScript ES6+ - Interatividade e comportamento dinâmico

Conceitos aprendidos

Este projeto demonstra:

- HTML semântico: Uso correto de tags como header, main, section
- CSS moderno: Flexbox, Grid, variáveis CSS, animações
- JavaScript vanilla: Manipulação do DOM, event listeners, animações
- Design responsivo: Site funciona em qualquer dispositivo
- Acessibilidade: Navegação por teclado, contraste adequado
- Performance: Código otimizado sem frameworks pesados

Para iniciantes

Se você está começando em desenvolvimento web, este projeto é perfeito porque:

1. Não usa frameworks complexos - apenas HTML, CSS e JS puros
2. Código bem comentado - cada parte é explicada
3. Conceitos fundamentais - ensina as bases do desenvolvimento web
4. Projeto real - não é apenas um tutorial, é um site funcional
5. Fácil de modificar - você pode experimentar e aprender

Como personalizar

Alterar cores:
/* No arquivo CSS, mude estas variáveis */
.site-header { background: #sua-cor-aqui; }
.hero h2 { color: #sua-cor-aqui; }

Adicionar novas seções:
<!-- No HTML, adicione uma nova seção -->
<section id="nova-secao" class="content-section">
  <h2>Nova Seção</h2>
  <p>Conteúdo da nova seção</p>
</section>

<!-- E um link no menu -->
<a href="#nova-secao">Nova Seção</a>

Modificar animações:
/* Mude a duração das transições */
transition: all 0.5s;  /* Era 0.3s, agora é 0.5s */

---

Desenvolvido com amor por Luis Henrique

Estudante de Análise e Desenvolvimento de Sistemas
Universidade Veiga de Almeida (2025)

Contato: lucoio@hotmail.com
GitHub: github.com/lucoio
