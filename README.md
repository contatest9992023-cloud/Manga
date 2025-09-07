```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MangaVerse - Leia Mangás Online</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2c3e50;
            --accent: #e74c3c;
            --dark: #1a1a2e;
            --light: #ecf0f1;
            --text: #333;
            --glow: #00ffff;
            --reader-bg: #0a0a1a;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--dark) 0%, #16213e 100%);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
            background-attachment: fixed;
        }
        
        /* Efeito de partículas no fundo */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        /* Header e Navegação */
        header {
            background: rgba(26, 26, 46, 0.8);
            backdrop-filter: blur(10px);
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }
        
        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 2rem;
            font-weight: 800;
            color: var(--light);
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo span {
            color: var(--accent);
        }
        
        .logo i {
            margin-right: 0.5rem;
            color: var(--accent);
        }
        
        .nav-menu {
            display: flex;
            list-style: none;
        }
        
        .nav-menu li {
            margin-left: 1.5rem;
        }
        
        .nav-menu a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            position: relative;
            padding: 0.5rem 0;
        }
        
        .nav-menu a:hover {
            color: var(--accent);
        }
        
        .nav-menu a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s;
        }
        
        .nav-menu a:hover::after {
            width: 100%;
        }
        
        .search-container {
            display: flex;
            align-items: center;
        }
        
        .search-box {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 25px;
            padding: 0.5rem 1rem;
            color: var(--light);
            outline: none;
            transition: all 0.3s;
            width: 250px;
        }
        
        .search-box:focus {
            border-color: var(--accent);
            box-shadow: 0 0 10px rgba(231, 76, 60, 0.5);
            width: 300px;
        }
        
        .search-btn {
            background: var(--accent);
            border: none;
            border-radius: 50%;
            width: 35px;
            height: 35px;
            margin-left: 0.5rem;
            color: white;
            cursor: pointer;
            transition: transform 0.3s;
        }
        
        .search-btn:hover {
            transform: scale(1.1);
        }
        
        /* Conteúdo Principal */
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        
        .hero {
            text-align: center;
            padding: 3rem 1rem;
            margin-bottom: 2rem;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(231, 76, 60, 0.1), transparent);
            transform: rotate(45deg);
            animation: shine 6s infinite;
        }
        
        @keyframes shine {
            0% {
                left: -50%;
            }
            100% {
                left: 150%;
            }
        }
        
        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, var(--light), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 2rem;
            color: #ccc;
        }
        
        .cta-btn {
            background: var(--accent);
            color: white;
            border: none;
            padding: 0.8rem 2rem;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(231, 76, 60, 0.4);
        }
        
        .cta-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(231, 76, 60, 0.6);
        }
        
        /* Seções de Mangás */
        .section-title {
            font-size: 2rem;
            margin: 3rem 0 1.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid var(--accent);
            display: inline-block;
        }
        
        .manga-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }
        
        .manga-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            position: relative;
            cursor: pointer;
        }
        
        .manga-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
        
        .manga-card img {
            width: 100%;
            height: 280px;
            object-fit: cover;
            transition: transform 0.5s;
        }
        
        .manga-card:hover img {
            transform: scale(1.05);
        }
        
        .manga-info {
            padding: 1rem;
        }
        
        .manga-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .manga-chapters, .manga-rating {
            font-size: 0.9rem;
            color: #aaa;
            display: flex;
            align-items: center;
            margin-bottom: 0.3rem;
        }
        
        .manga-chapters i, .manga-rating i {
            margin-right: 0.5rem;
            color: var(--accent);
        }
        
        .badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--accent);
            color: white;
            padding: 0.3rem 0.7rem;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: 600;
            z-index: 10;
        }
        
        .loading {
            text-align: center;
            padding: 2rem;
            font-size: 1.2rem;
            color: #aaa;
        }
        
        .loading i {
            margin-right: 0.5rem;
            color: var(--accent);
        }
        
        /* Modal de Detalhes */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            overflow-y: auto;
            padding: 2rem 0;
        }
        
        .modal-content {
            background: var(--dark);
            max-width: 800px;
            margin: 2rem auto;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.5);
        }
        
        .modal-header {
            padding: 1.5rem;
            background: rgba(0, 0, 0, 0.3);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-title {
            font-size: 1.5rem;
            font-weight: 600;
        }
        
        .close-btn {
            background: none;
            border: none;
            color: var(--light);
            font-size: 1.5rem;
            cursor: pointer;
            transition: color 0.3s;
        }
        
        .close-btn:hover {
            color: var(--accent);
        }
        
        .modal-body {
            padding: 1.5rem;
        }
        
        .modal-cover {
            width: 100%;
            max-width: 300px;
            border-radius: 5px;
            margin: 0 auto 1.5rem;
            display: block;
        }
        
        .modal-info h3 {
            margin: 1rem 0 0.5rem;
            color: var(--accent);
        }
        
        .modal-info p {
            margin-bottom: 1rem;
            color: #ccc;
        }
        
        .modal-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin: 1rem 0;
        }
        
        .modal-tag {
            background: rgba(231, 76, 60, 0.2);
            color: var(--accent);
            padding: 0.3rem 0.7rem;
            border-radius: 15px;
            font-size: 0.8rem;
        }
        
        /* Capítulos */
        .chapters-list {
            margin-top: 2rem;
        }
        
        .chapters-title {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--accent);
        }
        
        .chapter-item {
            background: rgba(255, 255, 255, 0.05);
            padding: 0.8rem 1rem;
            margin-bottom: 0.5rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .chapter-item:hover {
            background: rgba(231, 76, 60, 0.2);
        }
        
        /* Leitor de Mangá */
        .reader {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--reader-bg);
            z-index: 1100;
            overflow-y: auto;
        }
        
        .reader-header {
            background: rgba(0, 0, 0, 0.8);
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 10;
        }
        
        .reader-title {
            font-size: 1.2rem;
            font-weight: 600;
        }
        
        .reader-controls {
            display: flex;
            gap: 1rem;
        }
        
        .reader-controls button {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .reader-controls button:hover {
            background: var(--accent);
        }
        
        .reader-content {
            padding: 2rem;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .reader-page {
            max-width: 100%;
            margin-bottom: 1rem;
            border-radius: 5px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
        }
        
        .reader-page img {
            max-width: 100%;
            height: auto;
            display: block;
        }
        
        .reader-navigation {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 1.5rem;
            margin-bottom: 2rem;
        }
        
        /* Efeitos Glitch */
        .glitch-container {
            position: relative;
            display: inline-block;
        }
        
        .glitch {
            position: relative;
            display: inline-block;
        }
        
        .glitch::before, .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.8;
        }
        
        .glitch::before {
            animation: glitch-effect 3s infinite;
            color: #ff00ff;
            z-index: -1;
        }
        
        .glitch::after {
            animation: glitch-effect 2s infinite;
            color: #00ffff;
            z-index: -2;
        }
          @keyframes glitch-effect {
            0% {
                transform: translate(0);
            }
            20% {
                transform: translate(-5px, 5px);
            }
            40% {
                transform: translate(-5px, -5px);
            }
            60% {
                transform: translate(5px, 5px);
            }
            80% {
                transform: translate(5px, -5px);
            }
            100% {
                transform: translate(0);
            }
        }
        
        /* Footer */
        footer {
            background: rgba(26, 26, 46, 0.9);
            padding: 3rem 1rem;
            margin-top: 5rem;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }
        
        .footer-section h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            position: relative;
            padding-bottom: 0.5rem;
        }
        
        .footer-section h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50px;
            height: 2px;
            background: var(--accent);
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 0.8rem;
        }
        
        .footer-links a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: var(--accent);
        }
        
        .social-icons {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }
        
        .social-icons a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            transition: all 0.3s;
        }
        
        .social-icons a:hover {
            background: var(--accent);
            transform: translateY(-3px);
        }
        
        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 1.5rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #aaa;
            font-size: 0.9rem;
        }
        
        /* Responsividade */
        @media (max-width: 768px) {
            .nav-container {
                flex-direction: column;
            }
            
            .nav-menu {
                margin-top: 1rem;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .nav-menu li {
                margin: 0.5rem;
            }
            
            .hero h1 {
                font-size: 2.2rem;
            }
            
            .hero p {
                font-size: 1rem;
            }
            
            .manga-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            .search-box {
                width: 200px;
            }
            
            .search-box:focus {
                width: 200px;
            }
            
            .reader-header {
                flex-direction: column;
                gap: 1rem;
            }
            
            .reader-controls {
                flex-wrap: wrap;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- Efeito de partículas no fundo -->
    <div id="particles-js"></div>
    
    <!-- Cabeçalho com navegação -->
    <header>
        <div class="nav-container">
            <a href="#" class="logo">
                <i class="fas fa-dragon"></i>
                Manga<span>Verse</span>
            </a>
            
            <ul class="nav-menu">
                <li><a href="#">Início</a></li>
                <li><a href="#">Biblioteca</a></li>
                <li><a href="#">Categorias</a></li>
                <li><a href="#">Lançamentos</a></li>
                <li><a href="#">Sobre</a></li>
            </ul>
            
            <div class="search-container">
                <input type="text" class="search-box" placeholder="Buscar mangás..." id="search-input">
                <button class="search-btn" id="search-btn"><i class="fas fa-search"></i></button>
            </div>
        </div>
    </header>
    
    <!-- Conteúdo principal -->
    <div class="container">
        <section class="hero">
            <h1 class="glitch" data-text="Explore o Universo dos Mangás">Explore o Universo dos Mangás</h1>
            <p>Descubra os mangás mais populares do momento e fique por dentro dos últimos lançamentos. Leia capítulos diretamente no site.</p>
            <button class="cta-btn" id="refresh-btn">Atualizar Mangás</button>
        </section>
        
        <h2 class="section-title">Mangás em Alta <i class="fas fa-fire"></i></h2>
        <div class="manga-grid" id="popular-manga">
            <div class="loading">
                <i class="fas fa-spinner fa-spin"></i> Carregando mangás populares...
            </div>
        </div>
        
        <h2 class="section-title">Lançamentos Recentes <i class="fas fa-star"></i></h2>
        <div class="manga-grid" id="new-manga">
            <div class="loading">
                <i class="fas fa-spinner fa-spin"></i> Carregando lançamentos...
            </div>
        </div>
    </div>
    
    <!-- Modal para detalhes do mangá -->
    <div class="modal" id="manga-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title" id="modal-title">Título do Mangá</h2>
                <button class="close-btn" id="close-modal">&times;</button>
            </div>
            <div class="modal-body" id="modal-body">
                <!-- Conteúdo preenchido por JavaScript -->
            </div>
        </div>
    </div>
    
    <!-- Leitor de Mangá -->
    <div class="reader" id="manga-reader">
        <div class="reader-header">
            <h2 class="reader-title" id="reader-title">Capítulo do Mangá</h2>
            <div class="reader-controls">
                <button id="prev-page"><i class="fas fa-arrow-left"></i> Anterior</button>
                <button id="next-page">Próximo <i class="fas fa-arrow-right"></i></button>
                <button id="close-reader">Fechar Leitor</button>
            </div>
        </div>
        <div class="reader-content" id="reader-content">
            <!-- Conteúdo do capítulo será inserido aqui -->
        </div>
        <div class="reader-navigation">
            <button id="prev-chapter"><i class="fas fa-arrow-left"></i> Capítulo Anterior</button>
            <button id="next-chapter">Próximo Capítulo <i class="fas fa-arrow-right"></i></button>
        </div>
    </div>
    
    <!-- Rodapé -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>Sobre Nós</h3>
                <p>MangaVerse é a sua fonte definitiva para descobrir e ler mangás. Nosso sistema atualiza automaticamente com os conteúdos mais recentes e populares.</p>
            </div>
            
            <div class="footer-section">
                <h3>Links Rápidos</h3>
                <ul class="footer-links">
                    <li><a href="#">Política de Privacidade</a></li>
                    <li><a href="#">Termos de Serviço</a></li>
                    <li><a href="#">DMCA</a></li>
                    <li><a href="#">Contato</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Conecte-se Conosco</h3>
                <p>Siga-nos nas redes sociais para ficar por dentro das atualizações.</p>
                <div class="social-icons">
                    <a href="#"><i class="fab fa-facebook-f"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-discord"></i></a>
                </div>
            </div>
        </div>
        
        <div class="copyright">
            <p>&copy; 2023 MangaVerse. Todos os direitos reservados. Dados fornecidos por MangaDex e AniList.</p>
        </div>
    </footer>

    <script>
        // Elementos DOM
        const popularMangaContainer = document.getElementById('popular-manga');
        const newMangaContainer = document.getElementById('new-manga');
        const searchInput = document.getElementById('search-input');
        const searchBtn = document.getElementById('search-btn');
        const refreshBtn = document.getElementById('refresh-btn');
        const modal = document.getElementById('manga-modal');
        const modalTitle = document.getElementById('modal-title');
        const modalBody = document.getElementById('modal-body');
        const closeModal = document.getElementById('close-modal');
        const reader = document.getElementById('manga-reader');
        const readerTitle = document.getElementById('reader-title');
        const readerContent = document.getElementById('reader-content');
        const closeReader = document.getElementById('close-reader');
        const prevPageBtn = document.getElementById('prev-page');
        const nextPageBtn = document.getElementById('next-page');
        const prevChapterBtn = document.getElementById('prev-chapter');
        const nextChapterBtn = document.getElementById('next-chapter');

        // Variáveis globais
        let popularManga = [];
        let newManga = [];
        let currentManga = null;
        let currentChapter = null;
        let currentPage = 0;
        let chapterPages = [];

        // Função para buscar mangás populares da API do AniList
        async function fetchPopularManga() {
            try {
                const query = `
                    query {
                        Page(page: 1, perPage: 12) {
                            media(type: MANGA, sort: POPULARITY_DESC) {
                                id
                                title {
                                    romaji
                                    english
                                }
                                coverImage {
                                    large
                                }
                                meanScore
                                chapters
                                genres
                                description
                                siteUrl
                            }
                        }
                    }
                `;

                const response = await fetch('https://graphql.anilist.co', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Accept': 'application/json',
                    },
                    body: JSON.stringify({
                        query: query
                    })
                });

                const data = await response.json();
                return data.data.Page.media;
            } catch (error) {
                console.error('Erro ao buscar mangás populares:', error);
                return [];
            }
        }

        // Função para buscar mangás recentes da API do MangaDex
        async function fetchRecentManga() {
            try {
                const response = await fetch('https://api.mangadex.org/manga?limit=12&offset=0&order[latestUploadedChapter]=desc&includes[]=cover_art');
                const data = await response.json();
                
                return data.data.map(manga => {
                    const title = manga.attributes.title.en || 
                                 manga.attributes.title.ja || 
                                 manga.attributes.title['ja-ro'] || 
                                 Object.values(manga.attributes.title)[0];
                    
                    // Encontrar a relação de capa
                    const coverRelationship = manga.relationships.find(rel => rel.type === 'cover_art');
                    const coverFileName = coverRelationship ? coverRelationship.attributes.fileName : null;
                    const coverUrl = coverFileName ? `https://uploads.mangadex.org/covers/${manga.id}/${coverFileName}.256.jpg` : null;
                    
                    return {
                        id: manga.id,
                        title: title,
                        coverUrl: coverUrl,
                        lastChapter: manga.attributes.lastChapter,
                        tags: manga.attributes.tags.map(tag => tag.attributes.name.en),
                        description: manga.attributes.description?.en || 'Descrição não disponível',
                        isMangaDex: true
                    };
                });
            } catch (error) {
                console.error('Erro ao buscar mangás recentes:', error);
                return [];
            }
        }

        // Função para buscar capítulos de um mangá
        async function fetchChapters(mangaId) {
            try {
                const response = await fetch(`https://api.mangadex.org/manga/${mangaId}/feed?limit=50&translatedLanguage[]=pt-br&translatedLanguage[]=en&order[volume]=desc&order[chapter]=desc`);
                const data = await response.json();
                
                return data.data.map(chapter => {
                    return {
                        id: chapter.id,
                        chapter: chapter.attributes.chapter,
                        title: chapter.attributes.title,
                        pages: chapter.attributes.pages,
                        readableAt: chapter.attributes.readableAt
                    };
                });
            } catch (error) {
                console.error('Erro ao buscar capítulos:', error);
                return [];
            }
        }

        // Função para buscar páginas de um capítulo
        async function fetchChapterPages(chapterId) {
            try {
                const response = await fetch(`https://api.mangadex.org/at-home/server/${chapterId}`);
                const data = await response.json();
                
                return {
                    baseUrl: data.baseUrl,
                    chapter: data.chapter,
                    pages: data.chapter.data
                };
            } catch (error) {
                console.error('Erro ao buscar páginas do capítulo:', error);
                return null;
            }
        }

        // Função para buscar mangás por termo de pesquisa
        async function searchManga(query) {
            try {
                // Primeiro tenta na API do AniList
                const anilistQuery = `
                    query ($search: String) {
                        Page(page: 1, perPage: 20) {
                            media(type: MANGA, search: $search) {
                                id
                                title {
                                    romaji
                                    english
                                }
                                coverImage {
                                    large
                                }
                                meanScore
                                chapters
                                genres
                                description
                                siteUrl
                            }
                        }
                    }
                `;

                const response = await fetch('https://graphql.anilist.co', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Accept': 'application/json',
                    },
                    body: JSON.stringify({
                        query: anilistQuery,
                        variables: { search: query }
                    })
                });

                const data = await response.json();
                return data.data.Page.media;
            } catch (error) {
                console.error('Erro ao buscar mangás:', error);
                return [];
            }
        }

        // Função para gerar cards de mangá
        function generateMangaCards(mangaData, container, isPopular = true) {
            container.innerHTML = '';
            
            if (mangaData.length === 0) {
                container.innerHTML = '<div class="loading">Nenhum mangá encontrado.</div>';
                return;
            }
            
            mangaData.forEach(manga => {
                const card = document.createElement('div');
                card.className = 'manga-card';
                card.dataset.id = manga.id;
                
                const title = manga.title?.english || manga.title?.romaji || manga.title;
                const coverUrl = manga.coverImage?.large || manga.coverUrl || 'https://via.placeholder.com/200x300/2c3e50/ecf0f1?text=No+Image';
                const rating = manga.meanScore ? (manga.meanScore / 10).toFixed(1) : 'N/A';
                const chapters = manga.chapters || manga.lastChapter || 'N/A';
                const badge = isPopular ? 'Popular' : 'Novo';
                
                card.innerHTML = `
                    <div class="badge">${badge}</div>
                    <img src="${coverUrl}" alt="${title}" onerror="this.src='https://via.placeholder.com/200x300/2c3e50/ecf0f1?text=No+Image'">
                    <div class="manga-info">
                        <h3 class="manga-title">${title}</h3>
                        <div class="manga-chapters">
                            <i class="fas fa-book-open"></i>
                            <span>${chapters} Capítulos</span>
                        </div>
                        <div class="manga-rating">
                            <i class="fas fa-star"></i>
                            <span>${rating}</span>
                        </div>
                    </div>
                `;
                
                card.addEventListener('click', () => {
                    showMangaDetails(manga, isPopular);
                });
                
                container.appendChild(card);
            });
        }

        // Função para mostrar detalhes do mangá no modal
        async function showMangaDetails(manga, isPopular) {
            modalTitle.textContent = manga.title?.english || manga.title?.romaji || manga.title;
            const coverUrl = manga.coverImage?.large || manga.coverUrl || 'https://via.placeholder.com/200x300/2c3e50/ecf0f1?text=No+Image';
            const rating = manga.meanScore ? (manga.meanScore / 10).toFixed(1) : 'N/A';
            const chapters = manga.chapters || manga.lastChapter || 'N/A';
            const genres = manga.genres || manga.tags || [];
            const description = manga.description ? 
                manga.description.replace(/<[^>]*>/g, '').substring(0, 300) + '...' : 
                'Descrição não disponível.';
            
            let chaptersHTML = '';
            
            // Se for um mangá da MangaDex, buscar capítulos
            if (manga.isMangaDex) {
                chaptersHTML = '<div class="loading"><i class="fas fa-spinner fa-spin"></i> Carregando capítulos...</div>';
                modalBody.innerHTML = `
                    <img src="${coverUrl}" alt="${manga.title}" class="modal-cover" onerror="this.src='https://via.placeholder.com/300x450/2c3e50/ecf0f1?text=No+Image'">
                    <div class="modal-info">
                        <h3>Informações</h3>
                        <p><strong>Avaliação:</strong> ${rating}/10</p>
                        <p><strong>Capítulos:</strong> ${chapters}</p>
                        
                        <h3>Gêneros</h3>
                        <div class="modal-tags">
                            ${genres.slice(0, 5).map(genre => `<span class="modal-tag">${genre}</span>`).join('')}
                        </div>
                        
                        <h3>Sinopse</h3>
                        <p>${description}</p>
                        
                        <div class="chapters-list">
                            <h3 class="chapters-title">Capítulos</h3>
                            ${chaptersHTML}
                        </div>
                    </div>
                `;
                
                modal.style.display = 'block';
                document.body.style.overflow = 'hidden';
                
                // Buscar capítulos
                const chaptersList = await fetchChapters(manga.id);
                
                if (chaptersList.length > 0) {
                    chaptersHTML = chaptersList.map(chapter => `
                        <div class="chapter-item" data-id="${chapter.id}">
                            <strong>Capítulo ${chapter.chapter}</strong>${chapter.title ? `: ${chapter.title}` : ''}
                            <span style="float: right;">${new Date(chapter.readableAt).toLocaleDateString()}</span>
                        </div>
                    `).join('');
                } else {
                    chaptersHTML = '<p>Nenhum capítulo encontrado.</p>';
                }
                
                modalBody.innerHTML = `
                    <img src="${coverUrl}" alt="${manga.title}" class="modal-cover" onerror="this.src='https://via.placeholder.com/300x450/2c3e50/ecf0f1?text=No+Image'">
                    <div class="modal-info">
                        <h3>Informações</h3>
                        <p><strong>Avaliação:</strong> ${rating}/10</p>
                        <p><strong>Capítulos:</strong> ${chapters}</p>
                        
                        <h3>Gêneros</h3>
                        <div class="modal-tags">
                            ${genres.slice(0, 5).map(genre => `<span class="modal-tag">${genre}</span>`).join('')}
                        </div>
                        
                        <h3>Sinopse</h3>
                        <p>${description}</p>
                        
                        <div class="chapters-list">
                            <h3 class="chapters-title">Capítulos</h3>
                            ${chaptersHTML}
                        </div>
                    </div>
                `;
                
                // Adicionar event listeners aos capítulos
                const chapterItems = modalBody.querySelectorAll('.chapter-item');
                chapterItems.forEach(item => {
                    item.addEventListener('click', async () => {
                        const chapterId = item.dataset.id;
                        await openChapterReader(manga, chapterId, chaptersList);
                    });
                });
            } else {
                // Para mangás do AniList, não mostrar capítulos
                modalBody.innerHTML = `
                    <img src="${coverUrl}" alt="${manga.title}" class="modal-cover" onerror="this.src='https://via.placeholder.com/300x450/2c3e50/ecf0f1?text=No+Image'">
                    <div class="modal-info">
                        <h3>Informações</h3>
                        <p><strong>Avaliação:</strong> ${rating}/10</p>
                        <p><strong>Capítulos:</strong> ${chapters}</p>
                        
                        <h3>Gêneros</h3>
                        <div class="modal-tags">
                            ${genres.slice(0, 5).map(genre => `<span class="modal-tag">${genre}</span>`).join('')}
                        </div>
                        
                        <h3>Sinopse</h3>
                        <p>${description}</p>
                        
                        ${manga.siteUrl ? `<a href="${manga.siteUrl}" target="_blank" class="cta-btn" style="display: inline-block; margin-top: 1rem;">Ver na AniList</a>` : ''}
                    </div>
                `;
                
                modal.style.display = 'block';
                document.body.style.overflow = 'hidden';
            }
        }

        // Função para abrir o leitor de capítulo
        async function openChapterReader(manga, chapterId, chaptersList) {
            currentManga = manga;
            currentChapter = chaptersList.find(ch => ch.id === chapterId);
            currentPage = 0;
            
            readerTitle.textContent = `${manga.title?.english || manga.title?.romaji || manga.title} - Capítulo ${currentChapter.chapter}`;
            
            readerContent.innerHTML = '<div class="loading"><i class="fas fa-spinner fa-spin"></i> Carregando páginas...</div>';
            reader.style.display = 'block';
            document.body.style.overflow = 'hidden';
            modal.style.display = 'none';
            
            // Buscar páginas do capítulo
            const chapterData = await fetchChapterPages(chapterId);
            
            if (chapterData && chapterData.pages) {
                chapterPages = chapterData.pages;
                
                // Exibir a primeira página
                showPage(0);
                
                // Configurar navegação entre páginas
                prevPageBtn.onclick = () => showPage(currentPage - 1);
                nextPageBtn.onclick = () => showPage(currentPage + 1);
                
                // Configurar navegação entre capítulos
                const currentChapterIndex = chaptersList.findIndex(ch => ch.id === chapterId);
                prevChapterBtn.onclick = () => {
                    if (currentChapterIndex < chaptersList.length - 1) {
                        openChapterReader(manga, chaptersList[currentChapterIndex + 1].id, chaptersList);
                    }
                };
                
                nextChapterBtn.onclick = () => {
                    if (currentChapterIndex > 0) {
                        openChapterReader(manga, chaptersList[currentChapterIndex - 1].id, chaptersList);
                    }
                };
                
                // Mostrar/ocultar botões de navegação de capítulo
                prevChapterBtn.style.display = currentChapterIndex < chaptersList.length - 1 ? 'block' : 'none';
                nextChapterBtn.style.display = currentChapterIndex > 0 ? 'block' : 'none';
            } else {
                readerContent.innerHTML = '<div class="loading">Erro ao carregar o capítulo.</div>';
            }
        }

        // Função para exibir uma página específica
        function showPage(pageIndex) {
            if (pageIndex < 0 || pageIndex >= chapterPages.length) return;
            
            currentPage = pageIndex;
            
            // Construir URL da imagem
            const imageUrl = `https://uploads.mangadex.org/data/${chapterPages[pageIndex]}`;
            
            readerContent.innerHTML = `
                <div class="reader-page">
                    <img src="${imageUrl}" alt="Página ${pageIndex + 1}" onerror="this.src='https://via.placeholder.com/800x1200/2c3e50/ecf0f1?text=Página+${pageIndex + 1}'">
                </div>
                <p>Página ${pageIndex + 1} de ${chapterPages.length}</p>
            `;
            
            // Rolar para o topo da página
            readerContent.scrollTop = 0;
        }

        // Função para carregar todos os mangás
        async function loadAllManga() {
            popularMangaContainer.innerHTML = '<div class="loading"><i class="fas fa-spinner fa-spin"></i> Carregando mangás populares...</div>';
            newMangaContainer.innerHTML = '<div class="loading"><i class="fas fa-spinner fa-spin"></i> Carregando lançamentos...</div>';
            
            try {
                // Buscar dados das APIs em paralelo
                const [popularData, recentData] = await Promise.all([
                    fetchPopularManga(),
                    fetchRecentManga()
                ]);
                
                popularManga = popularData;
                newManga = recentData;
                
                generateMangaCards(popularManga, popularMangaContainer, true);
                generateMangaCards(newManga, newMangaContainer, false);
            } catch (error) {
                console.error('Erro ao carregar mangás:', error);
                popularMangaContainer.innerHTML = '<div class="loading">Erro ao carregar mangás. Tente novamente.</div>';
                newMangaContainer.innerHTML = '<div class="loading">Erro ao carregar lançamentos. Tente novamente.</div>';
            }
        }

        // Event Listeners
        searchBtn.addEventListener('click', async () => {
            const query = searchInput.value.trim();
            if (query) {
                popularMangaContainer.innerHTML = '<div class="loading"><i class="fas fa-spinner fa-spin"></i> Buscando mangás...</div>';
                const results = await searchManga(query);
                generateMangaCards(results, popularMangaContainer, false);
                newMangaContainer.innerHTML = '<div class="loading">Use a busca para encontrar mangás.</div>';
            }
        });

        searchInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                searchBtn.click();
            }
        });

        refreshBtn.addEventListener('click', loadAllManga);

        closeModal.addEventListener('click', () => {
            modal.style.display = 'none';
            document.body.style.overflow = 'auto';
        });

        closeReader.addEventListener('click', () => {
            reader.style.display = 'none';
            document.body.style.overflow = 'auto';
        });

        // Fechar modais clicando fora deles
        window.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.style.display = 'none';
                document.body.style.overflow = 'auto';
            }
            if (e.target === reader) {
                reader.style.display = 'none';
                document.body.style.overflow = 'auto';
            }
        });

        // Inicializar a página
        document.addEventListener('DOMContentLoaded', () => {
            loadAllManga();
            
            // Efeito de digitação no título
            const heroTitle = document.querySelector('.hero h1');
            const originalText = heroTitle.textContent;
            heroTitle.textContent = '';
            
            let i = 0;
            const typeWriter = () => {
                if (i < originalText.length) {
                    heroTitle.textContent += originalText.charAt(i);
                    i++;
                    setTimeout(typeWriter, 100);
                }
            };
            
            typeWriter();
        });

        // Simulação do particles.js para demonstração
        window.particlesJS = function(id, config) {
            console.log("Particles.js inicializado com sucesso!");
            const canvas = document.createElement('canvas');
            const ctx = canvas.getContext('2d');
            const container = document.getElementById(id);
            canvas.width = container.offsetWidth;
            canvas.height = container.offsetHeight;
            canvas.style.position = 'absolute';
            canvas.style.top = '0';
            canvas.style.left = '0';
            container.appendChild(canvas);
            
            // Simulação de partículas
            const particles = [];
            for (let i = 0; i < 50; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 3 + 1,
                    speedX: Math.random() * 2 - 1,
                    speedY: Math.random() * 2 - 1
                });
            }
            
            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                ctx.fillStyle = 'rgba(255, 255, 255, 0.5)';
                
                for (let i = 0; i < particles.length; i++) {
                    let p = particles[i];
                    p.x += p.speedX;
                    p.y += p.speedY;
                    
                    if (p.x < 0 || p.x > canvas.width) p.speedX *= -1;
                    if (p.y < 0 || p.y > canvas.height) p.speedY *= -1;
                    
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                    ctx.fill();
                }
                
                requestAnimationFrame(animate);
            }
            
            animate();
        };
    </script>
    
    <!-- Script de partículas (em produção, carregaria de CDN) -->
    <script>
        // Inicializar partículas
        document.addEventListener('DOMContentLoaded', () => {
            setTimeout(() => {
                if (typeof particlesJS !== 'undefined') {
                    particlesJS('particles-js', {
                        particles: {
                            number: { value: 80, density: { enable: true, value_area: 800 } },
                            color: { value: "#ffffff" },
                            opacity: { value: 0.5, random: true },
                            size: { value: 3, random: true },
                            line_linked: { enable: true, distance: 150, color: "#ffffff", opacity: 0.4, width: 1 },
                            move: { enable: true, speed: 2, direction: "none", random: true }
                        }
                    });
                }
            }, 1000);
        });
    </script>
</body>
</html>
