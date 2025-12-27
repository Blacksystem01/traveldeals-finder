html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TravelDeals Finder - Encontre as Melhores Ofertas de Viagem</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #f97316;
            --light: #f8fafc;
            --dark: #1e293b;
            --gray: #64748b;
            --success: #10b981;
            --shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        
        body {
            background-color: #f0f9ff;
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
            background-image: linear-gradient(rgba(255, 255, 255, 0.9), rgba(255, 255, 255, 0.9)), 
                              url('https://images.unsplash.com/photo-1488646953014-85cb44e25828?ixlib=rb-4.0.3&auto=format&fit=crop&w=1335&q=80');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background-color: white;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary);
        }
        
        .logo i {
            color: var(--secondary);
        }
        
        .nav-links {
            display: flex;
            gap: 25px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        /* Hero Section */
        .hero {
            padding: 80px 0 50px;
            text-align: center;
        }
        
        .hero h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            color: var(--dark);
            line-height: 1.2;
        }
        
        .hero p {
            font-size: 1.2rem;
            color: var(--gray);
            max-width: 700px;
            margin: 0 auto 40px;
        }
        
        /* Search Section */
        .search-container {
            background-color: white;
            border-radius: 16px;
            padding: 30px;
            box-shadow: var(--shadow);
            margin-bottom: 40px;
            max-width: 900px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .search-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: var(--dark);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .search-form {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
        }
        
        .form-group label {
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }
        
        .form-control {
            padding: 12px 15px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        .search-btn {
            grid-column: 1 / -1;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            padding: 15px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .search-btn:hover {
            background-color: var(--primary-dark);
        }
        
        /* Results Section */
        .results-container {
            margin-bottom: 60px;
        }
        
        .section-title {
            font-size: 2rem;
            margin-bottom: 30px;
            color: var(--dark);
            text-align: center;
            position: relative;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background-color: var(--secondary);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }
        
        .deals-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .deal-card {
            background-color: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .deal-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        .deal-image {
            height: 180px;
            width: 100%;
            object-fit: cover;
        }
        
        .deal-content {
            padding: 20px;
        }
        
        .deal-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }
        
        .deal-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--dark);
        }
        
        .deal-price {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--primary);
        }
        
        .deal-details {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .deal-detail {
            display: flex;
            align-items: center;
            gap: 5px;
            color: var(--gray);
            font-size: 0.9rem;
        }
        
        .deal-detail i {
            color: var(--primary);
        }
        
        .deal-description {
            color: var(--gray);
            margin-bottom: 20px;
            line-height: 1.5;
        }
        
        .deal-btn {
            display: block;
            width: 100%;
            background-color: var(--secondary);
            color: white;
            border: none;
            border-radius: 8px;
            padding: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
            text-align: center;
            text-decoration: none;
        }
        
        .deal-btn:hover {
            background-color: #ea580c;
        }
        
        /* Features */
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }
        
        .feature-card {
            background-color: white;
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
        }
        
        .feature-icon {
            background-color: #dbeafe;
            width: 70px;
            height: 70px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            font-size: 1.8rem;
            color: var(--primary);
        }
        
        .feature-title {
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: var(--dark);
        }
        
        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 50px 0 20px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            color: white;
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 10px;
        }
        
        .footer-links a {
            color: #cbd5e1;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: white;
        }
        
        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #334155;
            color: #cbd5e1;
            font-size: 0.9rem;
        }
        
        /* Responsividade */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            .hero h1 {
                font-size: 2.2rem;
            }
            
            .hero {
                padding: 50px 0 30px;
            }
            
            .search-container {
                padding: 20px;
            }
            
            .search-form {
                grid-template-columns: 1fr;
            }
            
            .deals-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Loading Animation */
        .loading {
            display: none;
            text-align: center;
            padding: 30px;
        }
        
        .spinner {
            border: 4px solid rgba(0, 0, 0, 0.1);
            border-radius: 50%;
            border-top: 4px solid var(--primary);
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* No Results */
        .no-results {
            text-align: center;
            padding: 40px;
            background-color: white;
            border-radius: 12px;
            box-shadow: var(--shadow);
            display: none;
        }
        
        .no-results i {
            font-size: 3rem;
            color: var(--gray);
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-plane-departure"></i>
                <span>TravelDeals Finder</span>
            </div>
            <nav class="nav-links">
                <a href="#"><i class="fas fa-home"></i> Início</a>
                <a href="#"><i class="fas fa-search"></i> Buscar</a>
                <a href="#"><i class="fas fa-heart"></i> Favoritos</a>
                <a href="#"><i class="fas fa-user"></i> Minha Conta</a>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1>Encontre as Melhores Ofertas de Viagem</h1>
            <p>Compare preços de passagens aéreas, hotéis e pacotes de viagem em um só lugar. Economize até 40% em suas próximas férias!</p>
        </div>
    </section>

    <!-- Search Section -->
    <section class="search">
        <div class="container">
            <div class="search-container">
                <h2 class="search-title"><i class="fas fa-search"></i> Encontre Sua Próxima Viagem</h2>
                <form id="searchForm" class="search-form">
                    <div class="form-group">
                        <label for="origin"><i class="fas fa-map-marker-alt"></i> Origem</label>
                        <input type="text" id="origin" class="form-control" placeholder="Cidade de origem" value="São Paulo">
                    </div>
                    
                    <div class="form-group">
                        <label for="destination"><i class="fas fa-location-arrow"></i> Destino</label>
                        <input type="text" id="destination" class="form-control" placeholder="Para onde você vai?">
                    </div>
                    
                    <div class="form-group">
                        <label for="departure"><i class="fas fa-calendar-alt"></i> Ida</label>
                        <input type="date" id="departure" class="form-control" value="2023-12-15">
                    </div>
                    
                    <div class="form-group">
                        <label for="return"><i class="fas fa-calendar-alt"></i> Volta</label>
                        <input type="date" id="return" class="form-control" value="2023-12-22">
                    </div>
                    
                    <div class="form-group">
                        <label for="travelers"><i class="fas fa-user-friends"></i> Viajantes</label>
                        <select id="travelers" class="form-control">
                            <option value="1">1 viajante</option>
                            <option value="2" selected>2 viajantes</option>
                            <option value="3">3 viajantes</option>
                            <option value="4">4 viajantes</option>
                            <option value="5">5+ viajantes</option>
                        </select>
                    </div>
                    
                    <button type="submit" class="search-btn">
                        <i class="fas fa-search"></i> Buscar Ofertas
                    </button>
                </form>
                <div class="loading" id="loading">
                    <div class="spinner"></div>
                    <p>Buscando as melhores ofertas para você...</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Results Section -->
    <section class="results">
        <div class="container results-container">
            <h2 class="section-title">Ofertas Recomendadas</h2>
            
            <div class="deals-grid" id="dealsGrid">
                <!-- As ofertas serão carregadas aqui via JavaScript -->
            </div>
            
            <div class="no-results" id="noResults">
                <i class="fas fa-search"></i>
                <h3>Nenhuma oferta encontrada</h3>
                <p>Tente ajustar seus critérios de busca para encontrar ofertas disponíveis.</p>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="features">
        <div class="container">
            <h2 class="section-title">Por que escolher o TravelDeals Finder?</h2>
            <div class="features">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-percentage"></i>
                    </div>
                    <h3 class="feature-title">Melhores Preços</h3>
                    <p>Garantimos os melhores preços do mercado ou devolvemos a diferença.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3 class="feature-title">Reserva Segura</h3>
                    <p>Suas informações estão protegidas com criptografia de ponta a ponta.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-headset"></i>
                    </div>
                    <h3 class="feature-title">Suporte 24/7</h3>
                    <p>Nossa equipe está disponível a qualquer hora para ajudar você.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>TravelDeals Finder</h3>
                    <p>Encontre as melhores ofertas de viagem com apenas alguns cliques. Economize tempo e dinheiro planejando suas férias conosco.</p>
                </div>
                
                <div class="footer-column">
                    <h3>Links Rápidos</h3>
                    <ul class="footer-links">
                        <li><a href="#">Início</a></li>
                        <li><a href="#">Buscar Ofertas</a></li>
                        <li><a href="#">Pacotes</a></li>
                        <li><a href="#">Hotéis</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Contato</h3>
                    <ul class="footer-links">
                        <li><i class="fas fa-envelope"></i> contato@traveldeals.com</li>
                        <li><i class="fas fa-phone"></i> (11) 99999-9999</li>
                        <li><i class="fas fa-map-marker-alt"></i> São Paulo, SP</li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2023 TravelDeals Finder. Todos os direitos reservados.</p>
            </div>
        </div>
    </footer>

    <script>
        // Dados de exemplo para as ofertas
        const sampleDeals = [
            {
                id: 1,
                title: "Rio de Janeiro - Pacote Completo",
                price: "R$ 1.899",
                image: "https://images.unsplash.com/photo-1483729558449-99ef09a8c325?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80",
                duration: "7 dias",
                travelers: "2 pessoas",
                description: "Voo + hotel 4 estrelas com café da manhã incluído. Ingresso para o Cristo Redentor e Pão de Açúcar.",
                type: "pacote"
            },
            {
                id: 2,
                title: "Fernando de Noronha - Mergulho",
                price: "R$ 3.499",
                image: "https://images.unsplash.com/photo-1590080667306-eb444a5c5c8a?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80",
                duration: "5 dias",
                travelers: "2 pessoas",
                description: "Pacote com mergulho incluso, hospedagem próxima à Praia do Sancho e translados.",
                type: "pacote"
            },
            {
                id: 3,
                title: "Salvador - História e Praias",
                price: "R$ 1.599",
                image: "https://images.unsplash.com/photo-1544984243-ec57ea16fe25?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80",
                duration: "6 dias",
                travelers: "2 pessoas",
                description: "Conheça o Pelourinho, faça passeio histórico e aproveite as melhores praias.",
                type: "pacote"
            },
            {
                id: 4,
                title: "Gramado - Romântico",
                price: "R$ 2.199",
                image: "https://images.unsplash.com/photo-1622037028967-4a7d0a5c54b4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80",
                duration: "5 dias",
                travelers: "2 pessoas",
                description: "Pacote romântico com hospedagem em chalé, jantar à luz de velas e passeio pela Rua Coberta.",
                type: "pacote"
            },
            {
                id: 5,
                title: "Bonito - Ecoturismo",
                price: "R$ 2.899",
                image: "https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?ixlib=rb-4.0.3&auto=format&fit=crop&w-1350&q=80",
                duration: "4 dias",
                travelers: "2 pessoas",
                description: "Flutuação, mergulho em rios cristalinos e visita às grutas. Inclui todas as atividades.",
                type: "pacote"
            },
            {
                id: 6,
                title: "Natal - Dunas e Praias",
                price: "R$ 1.799",
                image: "https://images.unsplash.com/photo-1544551763-46a013bb70d5?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80",
                duration: "6 dias",
                travelers: "2 pessoas",
                description: "Passeio de buggy pelas dunas, hospedagem em frente ao mar e café da manhã incluso.",
                type: "pacote"
            }
        ];

        // Elementos DOM
        const searchForm = document.getElementById('searchForm');
        const dealsGrid = document.getElementById('dealsGrid');
        const loading = document.getElementById('loading');
        const noResults = document.getElementById('noResults');

        // Inicializar com ofertas de exemplo
        document.addEventListener('DOMContentLoaded', function() {
            renderDeals(sampleDeals);
        });

        // Manipular envio do formulário
        searchForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Obter valores do formulário
            const origin = document.getElementById('origin').value;
            const destination = document.getElementById('destination').value;
            const departure = document.getElementById('departure').value;
            const travelers = document.getElementById('travelers').value;
            
            // Validar destino
            if (!destination) {
                alert("Por favor, informe um destino para sua viagem.");
                return;
            }
            
            // Mostrar carregamento
            loading.style.display = 'block';
            dealsGrid.innerHTML = '';
            noResults.style.display = 'none';
            
            // Simular busca com atraso (em um caso real, seria uma chamada API)
            setTimeout(() => {
                // Filtrar ofertas baseadas no destino (simulação)
                const filteredDeals = sampleDeals.filter(deal => {
                    return deal.title.toLowerCase().includes(destination.toLowerCase()) || 
                           destination.toLowerCase().includes("rio") && deal.title.includes("Rio") ||
                           destination.toLowerCase().includes("noronha") && deal.title.includes("Noronha") ||
                           destination.toLowerCase().includes("salvador") && deal.title.includes("Salvador") ||
                           destination.toLowerCase().includes("gramado") && deal.title.includes("Gramado") ||
                           destination.toLowerCase().includes("bonito") && deal.title.includes("Bonito") ||
                           destination.toLowerCase().includes("natal") && deal.title.includes("Natal");
                });
                
                // Ocultar carregamento
                loading.style.display = 'none';
                
                // Mostrar resultados
                if (filteredDeals.length > 0) {
                    renderDeals(filteredDeals);
                } else {
                    noResults.style.display = 'block';
                    dealsGrid.innerHTML = '';
                }
                
                // Rolar para os resultados
                document.querySelector('.results').scrollIntoView({ behavior: 'smooth' });
            }, 1500);
        });

        // Renderizar ofertas
        function renderDeals(deals) {
            dealsGrid.innerHTML = '';
            
            deals.forEach(deal => {
                const dealCard = document.createElement('div');
                dealCard.className = 'deal-card';
                
                dealCard.innerHTML = `
                    <img src="${deal.image}" alt="${deal.title}" class="deal-image">
                    <div class="deal-content">
                        <div class="deal-header">
                            <h3 class="deal-title">${deal.title}</h3>
                            <div class="deal-price">${deal.price}</div>
                        </div>
                        <div class="deal-details">
                            <div class="deal-detail">
                                <i class="far fa-calendar"></i>
                                <span>${deal.duration}</span>
                            </div>
                            <div class="deal-detail">
                                <i class="fas fa-user-friends"></i>
                                <span>${deal.travelers}</span>
                            </div>
                        </div>
                        <p class="deal-description">${deal.description}</p>
                        <a href="#" class="deal-btn">
                            <i class="fas fa-shopping-cart"></i> Reservar Agora
                        </a>
                    </div>
                `;
                
                dealsGrid.appendChild(dealCard);
            });
        }

        // Configurar datas mínimas no formulário
        const today = new Date();
        const tomorrow = new Date(today);
        tomorrow.setDate(tomorrow.getDate() + 1);
        
        const departureInput = document.getElementById('departure');
        const returnInput = document.getElementById('return');
        
        // Formatar datas para YYYY-MM-DD
        const formatDate = (date) => {
            return date.toISOString().split('T')[0];
        };
        
        departureInput.min = formatDate(today);
        returnInput.min = formatDate(tomorrow);
        
        // Se a data de ida for anterior a hoje, ajustar para hoje
        if (new Date(departureInput.value) < today) {
            departureInput.value = formatDate(today);
        }
        
        // Se a data de volta for anterior à data de ida, ajustar
        if (new Date(returnInput.value) <= new Date(departureInput.value)) {
            const nextDay = new Date(departureInput.value);
            nextDay.setDate(nextDay.getDate() + 1);
            returnInput.value = formatDate(nextDay);
        }
    </script>
</body>
</html># traveldeals-finder
