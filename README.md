<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>John In Flow | Social Media & Desenvolvedor Web</title>
    <!-- Open Graph Meta Tags -->
    <meta property="og:title" content="John In Flow | Social Media & Desenvolvedor Web">
    <meta property="og:description" content="Crio conteúdo que envolve, campanhas que vendem, fotos que contam histórias e sites que convertem.">
    <meta property="og:image" content="https://s11.aconvert.com/convert/p3r68-cdx67/hwxre-vqog7.jpg">
    <meta property="og:url" content="https://johninflow.com">
    <meta property="og:type" content="website">
    <!-- Meta tags de cartão do Twitter -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="John In Flow | Social Media & Desenvolvedor Web">
    <meta name="twitter:description" content="Crio conteúdo que engaja, campanhas que vendem, fotos que contam histórias e sites que convertem.">
    <meta name="twitter:image" content="https://s11.aconvert.com/convert/p3r68-cdx67/hwxre-vqog7.jpg">
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            scroll-behavior: smooth;
            background-color: #121212;
            color: #F5F5F5;
        }
        .neon-bg {
            background: linear-gradient(135deg, #2EC4B6 0%, #1A8A80 100%);
        }
        .neon-border {
            border: 2px solid #2EC4B6;
            box-shadow: 0 0 10px rgba(46, 196, 182, 0.5);
        }
        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 0 20px rgba(46, 196, 182, 0.7);
        }
        .project-card {
            transition: all 0.3s ease;
            background: #1E1E1E;
        }
        .project-card:hover {
            transform: scale(1.05);
            border-image: linear-gradient(135deg, #2EC4B6, #1A8A80) 1;
            box-shadow: 0 0 15px rgba(46, 196, 182, 0.5);
        }
        .floating {
            animation: neonPulse 2s ease-in-out infinite;
        }
        @keyframes neonPulse {
            0% {
                transform: translateY(0px);
                box-shadow: 0 0 10px rgba(46, 196, 182, 0.3);
            }
            50% {
                transform: translateY(-10px);
                box-shadow: 0 0 20px rgba(46, 196, 182, 0.7);
            }
            100% {
                transform: translateY(0px);
                box-shadow: 0 0 10px rgba(46, 196, 182, 0.3);
            }
        }
        .nav-link:hover {
            color: #2EC4B6;
            text-shadow: 0 0 5px rgba(46, 196, 182, 0.5);
        }
        .btn-neon {
            background-color: #2EC4B6;
            color: #121212;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        .btn-neon:hover {
            box-shadow: 0 0 15px rgba(46, 196, 182, 0.7);
            background-color: #3DE0D0;
        }
        /* Animação de fade-in para títulos */
        .fade-in {
            animation: fadeIn 1s ease-in-out;
        }
        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(20px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }
        /* Deslize para dentro do menu móvel */
        #mobile-menu {
            transform: translateX(100%);
            transition: transform 0.3s ease-in-out;
        }
        #mobile-menu.open {
            transform: translateX(0);
        }
        /* Botão Voltar ao Topo */
        #back-to-top {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #2EC4B6;
            color: #121212;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s ease;
            z-index: 100;
        }
        #back-to-top.visible {
            opacity: 1;
        }
        #back-to-top:hover {
            box-shadow: 0 0 15px rgba(46, 196, 182, 0.7);
            background-color: #3DE0D0;
        }
    </style>
</head>
<body>
    <!-- Navegação -->
    <nav class="fixed w-full bg-[#1E1E1E] shadow-md z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <a href="#" class="text-xl font-bold text-[#2EC4B6]" aria-label="Página inicial">John In Flow</a>
                </div>
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#about" class="text-[#F5F5F5] nav-link transition" aria-label="Sobre section">Sobre</a>
                    <a href="#services" class="text-[#F5F5F5] nav-link transition" aria-label="Serviços section">Serviços</a>
                    <a href="#skills" class="text-[#F5F5F5] nav-link transition" aria-label="Habilidades section">Habilidades</a>
                    <a href="#projetos" class="text-[#F5F5F5] nav-link transition" aria-label="Projetos section">Projetos</a>
                    <a href="#contact" class="btn-neon px-4 py-2 rounded-md" aria-label="Contato section">Contato</a>
                </div>
                <div class="md:hidden flex items-center">
                    <button id="menu-btn" class="text-[#F5F5F5]" aria-label="Alternar menu móvel">
                        <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
                        </svg>
                    </button>
                </div>
            </div>
        </div>
        <!-- Menu móvel -->
        <div id="mobile-menu" class="hidden md:hidden bg-[#1E1E1E] pb-4 px-4 shadow-lg">
            <a href="#about" class="block py-2 text-[#F5F5F5] nav-link transition" aria-label="Sobre section">Sobre</a>
            <a href="#services" class="block py-2 text-[#F5F5F5] nav-link transition" aria-label="Seção de serviços">Serviços</a>
            <a href="#skills" class="block py-2 text-[#F5F5F5] nav-link transition" aria-label="Seção de habilidades">Habilidades</a>
            <a href="#projetos" class="block py-2 text-[#F5F5F5] nav-link transition" aria-label="Seção de projetos">Projetos</a>
            <a href="#contact" class="block mt-2 btn-neon px-4 py-2 rounded-md text-center" aria-label="Seção de contato">Contato</a>
        </div>
    </nav>
    <!-- Seção Hero -->
    <section class="pt-24 pb-16 neon-bg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-2 gap-8 items-center">
                <div class="order-2 md:order-1">
                    <h1 class="text-4xl md:text-5xl font-extrabold mb-4 fade-in">John In Flow</h1>
                    <h2 class="text-xl md:text-2xl font-semibold mb-6 text-[#F5F5F5] fade-in">Social Media | Fotógrafo | Estrategista de Marketing Digital | Desenvolvedor Web</h2>
                    <p class="text-lg mb-8">"Crio conteúdo que engaja, campanhas que vendem, fotos que contam histórias e sites que convertem. Sou jovem, mas jogo como gente grande em mídias sociais, marketing digital, fotografia e desenvolvimento web."</p>
                    <div class="flex flex-wrap gap-4">
                        <a href="#contact" class="btn-neon px-6 py-3 rounded-md" aria-label="Fale comigo">Vamos conversar</a>
                        <a href="#projetos" class="neon-border text-[#F5F5F5] px-6 py-3 rounded-md font-medium hover:bg-[#2EC4B6] hover:text-[#121212] transition" aria-label="Ver projetos">Ver projetos</a>
                    </div>
                </div>
                <div class="order-1 md:order-2 flex justify-center">
                    <div class="relative w-64 h-64 md:w-80 md:h-80 rounded-full overflow-hidden neon-border floating">
                        <img src="https://s11.aconvert.com/convert/p3r68-cdx67/hwxre-vqog7.jpg" alt="Imagem de Perfil" class="w-full h-full object-cover" loading="lazy">
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Seção Sobre -->
    <section id="about" class="py-16 bg-[#1E1E1E]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12 text-[#F5F5F5] fade-in">Sobre Mim</h2>
            <div class="max-w-3xl mx-auto mb-12 text-gray-400 text-lg">
                <p>Eu sou o João (conhecido como John) - especialista em marketing digital e desenvolvedor web em construção constante. Meu ponto de virada não veio de uma sala de aula ou de um cliente grande, mas sim do voluntariado.</p>
                <p class="mt-4">Trabalhar com causas sociais me fez entender o verdadeiro poder da comunicação: não é só vender, é transformar realidades. Foi atuando em projetos voluntários que aprendi a gerenciar demandas sob pressão, criar sites com propósito, gerar conteúdo com impacto e fazer o pouco parecer muito.</p>
                <p class="mt-4">Com isso, desenvolvi uma habilidade essencial que falta em muita gente experiente: escuta ativa e adaptação rápida. Quando você trabalha com recursos limitados e pessoas diversas, aprende na marra a resolver problemas com criatividade e empatia.</p>
                <p class="mt-4">Hoje, trago essa bagagem para cada projeto que toco - unindo propósito, estratégia e execução digital. Meu objetivo é claro: ajudar marcas (e pessoas) a se posicionarem com relevância no meio digital, seja com design, conteúdo ou tecnologia.</p>
                <p class="mt-4 font-bold">Se você busca alguém com visão de futuro e valores sólidos, a conversa já começou.</p>
            </div>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-[#2A2A2A] p-6 rounded-lg shadow-sm neon-border">
                    <div class="text-[#2EC4B6] text-4xl mb-4">
                        <i class="fas fa-map-marker-alt"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Localização</h3>
                    <p class="text-gray-400">Horizontina/RS, Brasil</p>
                    <p class="text-gray-400">Atendo presencial e verbalmente</p>
                </div>
                <div class="bg-[#2A2A2A] p-6 rounded-lg shadow-sm neon-border">
                    <div class="text-[#2EC4B6] text-4xl mb-4">
                        <i class="fas fa-language"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Idiomas</h3>
                    <p class="text-gray-400">Português (nativo)</p>
                    <p class="text-gray-400">Inglês (fluente)</p>
                </div>
                <div class="bg-[#2A2A2A] p-6 rounded-lg shadow-sm neon-border">
                    <div class="text-[#2EC4B6] text-4xl mb-4">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Certificações</h3>
                    <ul class="list-disc list-inside text-gray-400 space-y-1">
                        <li>Marketing Digital – Google Activate</li>
                        <li>Marketing de Mídias Sociais – Meta Blueprint</li>
                        <li>Fotografia Digital – Coursera</li>
                        <li>Desenvolvimento Web Front-end – FreeCodeCamp</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>
    <!-- Seção de Serviços -->
    <section id="services" class="py-16 bg-[#121212]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-4 text-[#F5F5F5] fade-in">Serviços</h2>
            <p class="text-center text-gray-400 mb-12 max-w-3xl mx-auto">Ofereço soluções completas para sua presença digital e aumentar seus resultados</p>
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Service 1 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-hashtag"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Criação de Conteúdo</h3>
                    <p class="text-gray-400">Conteúdo estratégico para redes sociais (imagem, vídeo e texto) que engajam seu público-alvo e fortalecem sua marca.</p>
                </div>
                <!-- Serviço 2 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-chess"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Estratégias de Social Media</h3>
                    <p class="text-gray-400">Planejamento e execução de estratégias personalizadas para aumentar seu alcance e engajamento nas redes sociais.</p>
                </div>
                <!-- Service 3 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-camera"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Fotografia Profissional</h3>
                    <p class="text-gray-400">Fotos de alta qualidade (lifestyle, produtos, eventos) que contam a história da sua marca de forma visualmente impactante.</p>
                </div>
                <!-- Service 4 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-film"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Edição de Vídeos</h3>
                    <p class="text-gray-400">Edição profissional de reels, stories e TikToks que capturam a atenção do seu público e aumentam o engajamento.</p>
                </div>
                <!-- Service 5 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-bullseye"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Marketing Digital</h3>
                    <p class="text-gray-400">Gestão completa de campanhas (orgânicas e pagas) com análise de dados e otimização contínua para melhores resultados.</p>
                </div>
                <!-- Serviço 6 -->
                <div class="bg-[#2A2A2A] p-6 rounded-lg service-card transition duration-300 neon-border">
                    <div class="text-[#2EC4B6] text-3xl mb-4">
                        <i class="fas fa-code"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-[#F5F5F5]">Desenvolvimento Web</h3>
                    <p class="text-gray-400">Criação de sites responsivos e personalizados que convertem visitantes em clientes, usando HTML, CSS, JavaScript ou plataformas como Wix e Nuvemshop.</p>
                </div>
            </div>
        </div>
    </section>
    <!-- Skills Section -->
    <section id="skills" class="py-16 bg-[#1E1E1E]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12 text-[#F5F5F5] fade-in">Habilidades e Ferramentas</h2>
            <div class="grid md:grid-cols-2 gap-8">
                <!-- Habilidades -->
                <div>
                    <h3 class="text-xl font-semibold mb-6 text-[#2EC4B6]">Principais Habilidades</h3>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-[#F5F5F5]">Planejamento estratégico</span>
                                <span class="text-gray-400">95%</span>
                            </div>
                            <div class="w-full bg-[#2A2A2A] rounded-full h-2.5">
                                <div class="bg-[#2EC4B6] h-2.5 rounded-full" style="width: 95%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-[#F5F5F5]">Redação</span>
                                <span class="text-gray-400">90%</span>
                            </div>
                            <div class="w-full bg-[#2A2A2A] rounded-full h-2.5">
                                <div class="bg-[#2EC4B6] h-2.5 rounded-full" style="width: 90%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-[#F5F5F5]">Fotografia e edição</span>
                                <span class="text-gray-400">92%</span>
                            </div>
                            <div class="w-full bg-[#2A2A2A] rounded-full h-2.5">
                                <div class="bg-[#2EC4B6] h-2.5 rounded-full" style="width: 92%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-[#F5F5F5]">Edição de vídeo</span>
                                <span class="text-gray-400">88%</span>
                            </div>
                            <div class="w-full bg-[#2A2A2A] rounded-full h-2.5">
                                <div class="bg-[#2EC4B6] h-2.5 rounded-full" style="width: 88%"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1">
                                <span class="text-[#F5F5F5]">Desenvolvimento Web</span>
                                <span class="text-gray-400">85%</span>
                            </div>
                            <div class="w-full bg-[#2A2A2A] rounded-full h-2.5">
                                <div class="bg-[#2EC4B6] h-2.5 rounded-full" style="width: 85%"></div>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- Ferramentas -->
                <div>
                    <h3 class="text-xl font-semibold mb-6 text-[#2EC4B6]">Ferramentas de Domínio</h3>
                    <div class="flex flex-wrap gap-3">
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Lightroom</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Photoshop</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Canva</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">CapCut</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">InShot</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Meta Business Suite</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Análise do TikTok</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Notion</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Trello</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">DSLR</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">HTML/CSS/JS</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Wix</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Nuvemshop</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Figma</span>
                        <span class="bg-[#2A2A2A] text-[#F5F5F5] px-3 py-1 rounded-full text-sm neon-border">Google Analytics</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Seção Projetos -->
    <section id="projetos" class="py-16 bg-[#121212]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-4 text-[#F5F5F5] fade-in">Projetos Realizados</h2>
            <p class="text-center text-gray-400 mb-12 max-w-3xl mx-auto">Alguns dos trabalhos que realizei para clientes e os resultados alcançados</p>
            <div class="grid md:grid-cols-2 gap-8">
                <!-- Projeto 1 -->
                <div class="rounded-lg project-card neon-border">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Imagem Pública</h3>
                        <p class="text-gray-400 mb-4">@interacthz | Out 2019 - Atual</p>
                        <p class="text-gray-400">Gestão completa de redes sociais, criação de conteúdo estratégico e desenvolvimento de campanhas que aumentaram o engajamento em 150%.</p>
                    </div>
                </div>
                <!-- Project 2 -->
                <div class="rounded-lg project-card neon-border">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Analista de Marketing Institucional</h3>
                        <p class="text-gray-400 mb-4">@cfjlhz e @fahorhz | Jan 2023 - Dez 2023 | Fev 2025 - Abr 2025</p>
                        <p class="text-gray-400">Desenvolvimento e implementação de estratégias de marketing digital que resultaram em aumento de 80% no alcance orgânico.</p>
                    </div>
                </div>
                <!-- Project 3 -->
                <div class="rounded-lg project-card neon-border">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Mídias Sociais de Marketing Esportivo</h3>
                        <p class="text-gray-400 mb-4">@acehor_hz | Mar 2024 - Fev 2025</p>
                        <p class="text-gray-400">Criação de conteúdo viral esportivo que aumentou o número de seguidores em 300% em 6 meses.</p>
                    </div>
                </div>
                <!-- Project 4 -->
                <div class="rounded-lg project-card neon-border">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2 text-[#F5F5F5]">Marketing e Desenvolvedor Web</h3>
                        <p class="text-gray-400 mb-4">@lojao.agrícola e @planasul | Abr 2025 - Atual</p>
                        <p class="text-gray-400">Desenvolvimento de sites e estratégias de marketing digital que aumentaram as vendas online em 200% no primeiro trimestre.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Seção de Depoimentos -->
    <section class="py-16 neon-bg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12 text-[#F5F5F5] fade-in">Depoimentos</h2>
            <div class="max-w-3xl mx-auto text-center">
                <div class="mb-8 text-5xl">
                    <i class="fas fa-quote-left text-[#1A8A80]"></i>
                </div>
                <p class="text-xl mb-8 italic text-[#F5F5F5]">"Quer ser o próximo a ter resultados reais? Vamos trabalhar juntos - seu depoimento pode ser o próximo destaque aqui!"</p>
            </div>
        </div>
    </section>
    <!-- Seção de contato -->
    <section id="contact" class="py-16 bg-[#1E1E1E]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-4 text-[#F5F5F5] fade-in">Vamos Trabalhar Juntos</h2>
            <p class="text-center text-gray-400 mb-12 max-w-3xl mx-auto">"Quer transformar sua marca com estratégias reais e conteúdo de impacto? Vamos conversar!"</p>
            <div class="grid md:grid-cols-2 gap-12">
                <div>
                    <h3 class="text-xl font-semibold mb-6 text-[#2EC4B6]">Informações de Contato</h3>
                    <div class="space-y-6">
                        <div class="flex items-start">
                            <div class="text-[#2EC4B6] text-xl mr-4 mt-1">
                                <i class="fas fa-envelope"></i>
                            </div>
                            <div>
                                <h4 class="font-medium text-[#F5F5F5]">E-mail</h4>
                                <a href="mailto:jk006434@cfjl.com.br" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="E-mail: jk006434@cfjl.com.br">jk006434@cfjl.com.br</a>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-[#2EC4B6] text-xl mr-4 mt-1">
                                <i class="fab fa-whatsapp"></i>
                            </div>
                            <div>
                                <h4 class="font-medium text-[#F5F5F5]">WhatsApp</h4>
                                <a href="https://wa.me/555592209649" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="WhatsApp: +55 (55) 9 9220-9649">+55 (55) 9 9220-9649</a>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-[#2EC4B6] text-xl mr-4 mt-1">
                                <i class="fab fa-linkedin"></i>
                            </div>
                            <div>
                                <h4 class="font-medium text-[#F5F5F5]">LinkedIn</h4>
                                <a href="https://www.linkedin.com/in/johnnhdk/" target="_blank" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="Perfil do LinkedIn">linkedin.com/in/johnnhdk</a>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-[#2EC4B6] text-xl mr-4 mt-1">
                                <i class="fab fa-instagram"></i>
                            </div>
                            <div>
                                <h4 class="font-medium text-[#F5F5F5]">Instagram Profissional</h4>
                                <a href="https://www.instagram.com/johnnflow/" target="_blank" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="Instagram: @johnnflow">@johnnflow</a>
                            </div>
                        </div>
                    </div>
                </div>
                <div>
                    <h3 class="text-xl font-semibold mb-6 text-[#2EC4B6]">Enviar uma mensagem</h3>
                    <form id="contact-form" class="space-y-4">
                        <div>
                            <label for="name" class="block text-sm font-medium text-[#F5F5F5] mb-1">Nome</label>
                            <input type="text" id="name" name="name" class="w-full px-4 py-2 bg-[#2A2A2A] border border-[#2EC4B6] rounded-md focus:ring-[#2EC4B6] focus:border-[#3DE0D0] text-[#F5F5F5]" required aria-required="true" aria-label="Seu nome">
                        </div>
                        <div>
                            <label for="email" class="block text-sm font-medium text-[#F5F5F5] mb-1">E-mail</label>
                            <input type="email" id="email" name="email" class="w-full px-4 py-2 bg-[#2A2A2A] border border-[#2EC4B6] rounded-md focus:ring-[#2EC4B6] focus:border-[#3DE0D0] text-[#F5F5F5]" required aria-required="true" aria-label="Seu e-mail">
                        </div>
                        <div>
                            <label for="subject" class="block text-sm font-medium text-[#F5F5F5] mb-1">Assunto</label>
                            <input type="text" id="subject" name="subject" class="w-full px-4 py-2 bg-[#2A2A2A] border border-[#2EC4B6] rounded-md focus:ring-[#2EC4B6] focus:border-[#3DE0D0] text-[#F5F5F5]" required aria-required="true" aria-label="Assunto">
                        </div>
                        <div>
                            <label for="message" class="block text-sm font-medium text-[#F5F5F5] mb-1">Mensagem</label>
                            <textarea id="message" name="message" rows="4" class="w-full px-4 py-2 bg-[#2A2A2A] border border-[#2EC4B6] rounded-md focus:ring-[#2EC4B6] focus:border-[#3DE0D0] text-[#F5F5F5]" required aria-required="true" aria-label="Sua mensagem"></textarea>
                        </div>
                        <button type="submit" class="btn-neon px-6 py-3 rounded-md w-full" aria-label="Enviar mensagem para WhatsApp">Enviar mensagem</button>
                    </form>
                </div>
            </div>
        </div>
    </section>
    <!-- Botão Voltar ao Topo -->
    <button id="back-to-top" aria-label="Voltar ao topo">
        <i class="fas fa-arrow-up"></i>
    </button>
    <!-- Rodapé -->
    <footer class="bg-[#1E1E1E] text-[#F5F5F5] py-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-4 md:mb-0">
                    <a href="#" class="text-xl font-bold text-[#2EC4B6]" aria-label="Página inicial">John In Flow</a>
                    <p class="text-gray-400 mt-1">Mídias sociais | Fotógrafo | Estrategista de marketing digital | Desenvolvedor web</p>
                </div>
                <div class="flex space-x-6">
                    <a href="https://www.linkedin.com/in/johnnhdk/" target="_blank" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="Perfil do LinkedIn">
                        <i class="fab fa-linkedin text-2xl"></i>
                    </a>
                    <a href="https://www.instagram.com/johnnflow/" target="_blank" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="Perfil do Instagram">
                        <i class="fab fa-instagram text-2xl"></i>
                    </a>
                    <a href="mailto:jk006434@cfjl.com.br" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="E-mail">
                        <i class="fas fa-envelope text-2xl"></i>
                    </a>
                    <a href="https://wa.me/555592209649" class="text-gray-400 hover:text-[#2EC4B6] transition" aria-label="WhatsApp">
                        <i class="fab fa-whatsapp text-2xl"></i>
                    </a>
                </div>
            </div>
            <div class="border-t border-[#2EC4B6] mt-8 pt-8 text-center text-gray-400">
                <p>© 2023 John In Flow. Todos os direitos reservados.</p>
            </div>
        </div>
    </footer>
    <script>
        // Alternância de menu móvel com animação deslizante
        const menuBtn = document.getElementById('menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        menuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
            mobileMenu.classList.toggle('open');
        });
        // Rolagem suave para links de âncora
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    // Fechar menu móvel se estiver aberto
                    if (!mobileMenu.classList.contains('hidden')) {
                        mobileMenu.classList.add('hidden');
                        mobileMenu.classList.remove('open');
                    }
                }
            });
        });
        // Envio de formulário com redirecionamento do WhatsApp
        const form = document.getElementById('contact-form');
        if (form) {
            form.addEventListener('submit', (e) => {
                e.preventDefault();
                const name = form.querySelector('#name').value.trim();
                const email = form.querySelector('#email').value.trim();
                const subject = form.querySelector('#subject').value.trim();
                const message = form.querySelector('#message').value.trim();
                if (name && email && subject && message) {
                    const whatsappMessage = `Olá, sou ${name}. Meu e-mail é ${email}. Assunto: ${subject}. Mensagem: ${message}`;
                    const encodedMessage = encodeURIComponent(whatsappMessage);
                    const whatsappUrl = `https://wa.me/555592209649?text=${encodedMessage}`;
                    window.open(whatsappUrl, '_blank');
                    form.reset();
                } else {
                    alert('Por favor, preencha todos os campos.');
                }
            });
        }
        // Visibilidade do botão Voltar ao Topo
        const backToTop = document.getElementById('back-to-top');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                backToTop.classList.add('visible');
            } else {
                backToTop.classList.remove('visible');
            }
        });
        backToTop.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        // Verifica o carregamento da imagem do perfil
        const profileImg = document.querySelector('.floating img');
        profileImg.addEventListener('error', () => {
            console.error('Erro ao carregar a imagem do perfil. Verifique a URL: https://s11.aconvert.com/convert/p3r68-cdx67/hwxre-vqog7.jpg');
        });
    </script>
</body>
</html>
