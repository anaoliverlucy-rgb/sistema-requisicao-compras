<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Requisição de Compras - CP Karabet</title>
    <link rel="icon" type="image/x-icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>📋</text></svg>">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: rgba(44, 62, 80, 0.95);
            color: white;
            padding: 20px 0;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            backdrop-filter: blur(10px);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }
        
        h1 {
            font-size: 24px;
            font-weight: 600;
            margin: 10px 0;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
            color: white;
        }
        
        .logout-btn {
            background: rgba(255,255,255,0.2);
            color: white;
            border: 1px solid rgba(255,255,255,0.3);
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .logout-btn:hover {
            background: rgba(255,255,255,0.3);
        }
        
        .card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
            margin-bottom: 25px;
            overflow: hidden;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .card-header {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            padding: 18px 25px;
            font-weight: 600;
            font-size: 18px;
        }
        
        .card-body {
            padding: 25px;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: #2c3e50;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px 18px;
            border: 2px solid #e1e8ed;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }
        
        .form-row {
            display: flex;
            flex-wrap: wrap;
            margin: 0 -12px;
        }
        
        .form-col {
            flex: 1;
            padding: 0 12px;
            min-width: 280px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        th, td {
            padding: 14px 18px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background: linear-gradient(135deg, #34495e, #2c3e50);
            color: white;
            font-weight: 600;
        }
        
        tr:hover {
            background-color: #f8f9fa;
        }
        
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(52, 152, 219, 0.3);
        }
        
        .btn-success {
            background: linear-gradient(135deg, #2ecc71, #27ae60);
            color: white;
        }
        
        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(46, 204, 113, 0.3);
        }
        
        .btn-danger {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
        }
        
        .btn-danger:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(231, 76, 60, 0.3);
        }
        
        .btn-warning {
            background: linear-gradient(135deg, #f39c12, #e67e22);
            color: white;
        }
        
        .btn-warning:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(243, 156, 18, 0.3);
        }
        
        .btn-sm {
            padding: 8px 16px;
            font-size: 14px;
        }
        
        .actions {
            display: flex;
            gap: 15px;
            justify-content: flex-end;
            margin-top: 25px;
            flex-wrap: wrap;
        }
        
        .item-row {
            display: flex;
            margin-bottom: 18px;
            gap: 15px;
            align-items: flex-end;
            padding: 15px;
            background: #f8f9fa;
            border-radius: 8px;
            border-left: 4px solid #3498db;
        }
        
        .item-desc {
            flex: 3;
        }
        
        .item-qty {
            flex: 1;
        }
        
        .item-actions {
            flex: 0 0 120px;
        }
        
        .instructions {
            background: #e8f4fc;
            border-left: 4px solid #3498db;
            padding: 15px 20px;
            margin-bottom: 20px;
            border-radius: 0 8px 8px 0;
        }
        
        .instructions h3 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .instructions ul {
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
            color: #555;
        }
        
        .login-container {
            max-width: 400px;
            margin: 100px auto;
            padding: 30px;
        }
        
        .login-form {
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        }
        
        .login-title {
            text-align: center;
            margin-bottom: 30px;
            color: #2c3e50;
        }
        
        .user-type-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .user-type-btn {
            flex: 1;
            padding: 12px;
            border: 2px solid #e1e8ed;
            background: white;
            border-radius: 8px;
            cursor: pointer;
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .user-type-btn.active {
            border-color: #3498db;
            background: #3498db;
            color: white;
        }
        
        .hidden {
            display: none !important;
        }
        
        .requisicao-detalhes {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .status-badge {
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
        }
        
        .status-pendente {
            background: #fff3cd;
            color: #856404;
        }
        
        .status-aprovado {
            background: #d1ecf1;
            color: #0c5460;
        }
        
        .status-rejeitado {
            background: #f8d7da;
            color: #721c24;
        }
        
        .status-finalizado {
            background: #d4edda;
            color: #155724;
        }
        
        .admin-actions {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }
        
        @media (max-width: 768px) {
            .form-col {
                flex: 100%;
            }
            
            .item-row {
                flex-direction: column;
                align-items: stretch;
                gap: 12px;
            }
            
            .item-actions {
                display: flex;
                gap: 10px;
            }
            
            .actions {
                justify-content: stretch;
            }
            
            .actions .btn {
                flex: 1;
                justify-content: center;
            }
            
            .header-content {
                flex-direction: column;
                text-align: center;
                gap: 10px;
            }
            
            .user-info {
                flex-direction: column;
                gap: 10px;
            }
        }
        
        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: #7f8c8d;
        }
        
        .empty-state i {
            font-size: 48px;
            margin-bottom: 15px;
            display: block;
        }
    </style>
</head>
<body>
    <!-- Tela de Login -->
    <div id="login-screen" class="login-container">
        <div class="login-form">
            <h2 class="login-title">📋 Sistema de Compras<br><small>CP Karabet</small></h2>
            
            <div class="user-type-selector">
                <div class="user-type-btn active" data-type="solicitante">Solicitante</div>
                <div class="user-type-btn" data-type="admin">Administrador</div>
            </div>
            
            <div class="form-group">
                <label for="login-username">Usuário:</label>
                <input type="text" id="login-username" placeholder="Digite seu usuário">
            </div>
            
            <div class="form-group">
                <label for="login-password">Senha:</label>
                <input type="password" id="login-password" placeholder="Digite sua senha">
            </div>
            
            <button type="button" id="btn-login" class="btn btn-success" style="width: 100%;">
                🔑 Entrar no Sistema
            </button>
            
            <div style="margin-top: 20px; padding: 15px; background: #f8f9fa; border-radius: 6px; font-size: 12px;">
                <strong>Credenciais de Teste:</strong><br>
                <strong>Solicitante:</strong> usuario / senha123<br>
                <strong>Admin:</strong> admin / admin123
            </div>
        </div>
    </div>

    <!-- Sistema Principal (Após Login) -->
    <div id="main-system" class="hidden">
        <header>
            <div class="container">
                <div class="header-content">
                    <div class="logo">
                        <span>📋</span>
                        Sistema de Compras - CP Karabet
                    </div>
                    <h1>Requisição de Compras - Materiais Diversos</h1>
                    <div class="user-info">
                        <span>👤 Logado como: <strong id="current-user"></strong></span>
                        <span id="user-role-badge"></span>
                        <button type="button" id="btn-logout" class="logout-btn">🚪 Sair</button>
                    </div>
                </div>
            </div>
        </header>
        
        <div class="container">
            <!-- Área do Solicitante -->
            <div id="solicitante-area" class="hidden">
                <div class="instructions">
                    <h3>📝 Como usar o sistema:</h3>
                    <ul>
                        <li>Preencha todos os campos obrigatórios</li>
                        <li>Adicione os itens necessários usando o botão "Adicionar Item"</li>
                        <li>Clique em "Enviar Requisição" para finalizar</li>
                        <li>Acompanhe o status no histórico abaixo</li>
                    </ul>
                </div>
                
                <div class="card">
                    <div class="card-header">📋 Nova Requisição</div>
                    <div class="card-body">
                        <div class="form-row">
                            <div class="form-col">
                                <div class="form-group">
                                    <label for="solicitante">👤 Solicitante:</label>
                                    <input type="text" id="solicitante" placeholder="Seu nome completo" required>
                                </div>
                            </div>
                            <div class="form-col">
                                <div class="form-group">
                                    <label for="data">📅 Data:</label>
                                    <input type="date" id="data" required>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="loja-vd">🏪 Qual Loja ou VD que irá utilizar?</label>
                            <select id="loja-vd" required>
                                <option value="">Selecione uma opção</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label>🛍️ Itens Solicitados:</label>
                            <div id="itens-container">
                                <div class="item-row">
                                    <div class="item-desc">
                                        <input type="text" class="item-descricao" placeholder="Descrição do Material e/ou Produto" required>
                                    </div>
                                    <div class="item-qty">
                                        <input type="number" class="item-quantidade" placeholder="Quantidade" min="1" required>
                                    </div>
                                    <div class="item-actions">
                                        <button type="button" class="btn btn-danger btn-remover-item btn-sm">🗑️ Remover</button>
                                    </div>
                                </div>
                            </div>
                            <button type="button" id="btn-adicionar-item" class="btn btn-primary">➕ Adicionar Item</button>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-col">
                                <div class="form-group">
                                    <label for="voltagem">⚡ Qual Voltagem?</label>
                                    <select id="voltagem">
                                        <option value="">Selecione</option>
                                        <option value="110V">110V</option>
                                        <option value="220V">220V</option>
                                        <option value="Bivolt">Bivolt</option>
                                        <option value="Outra">Outra</option>
                                    </select>
                                </div>
                            </div>
                            <div class="form-col">
                                <div class="form-group">
                                    <label for="link-foto">🔗 Link do Material e/ou Produto ou Foto:</label>
                                    <input type="text" id="link-foto" placeholder="URL ou descrição da foto">
                                </div>
                            </div>
                        </div>
                        
                        <div class="actions">
                            <button type="button" id="btn-limpar" class="btn btn-danger">🧹 Limpar</button>
                            <button type="button" id="btn-enviar" class="btn btn-success">📤 Enviar Requisição</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Área do Administrador -->
            <div id="admin-area" class="hidden">
                <div class="instructions">
                    <h3>👨‍💼 Painel do Administrador</h3>
                    <ul>
                        <li>Visualize todas as requisições do sistema</li>
                        <li>Clique em "Ver Detalhes" para analisar cada requisição</li>
                        <li>Altere o status conforme a análise</li>
                        <li>Adicione observações quando necessário</li>
                    </ul>
                </div>
            </div>

            <!-- Histórico de Requisições (Compartilhado) -->
            <div class="card" id="historico-section">
                <div class="card-header">
                    📊 Histórico de Requisições
                    <span id="historico-subtitle" style="font-size: 14px; opacity: 0.8; margin-left: 10px;"></span>
                </div>
                <div class="card-body">
                    <table id="tabela-historico">
                        <thead>
                            <tr>
                                <th>📅 Data</th>
                                <th>👤 Solicitante</th>
                                <th>🏪 Loja/VD</th>
                                <th>🛍️ Itens</th>
                                <th>📋 Status</th>
                                <th>Ações</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td colspan="6">
                                    <div class="empty-state">
                                        <i>📝</i>
                                        <p>Nenhuma requisição encontrada</p>
                                        <small>As requisições aparecerão aqui após o envio</small>
                                    </div>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Modal de Detalhes da Requisição -->
            <div id="modal-detalhes" class="hidden">
                <div class="card">
                    <div class="card-header">
                        📄 Detalhes da Requisição
                        <button type="button" id="btn-fechar-modal" class="logout-btn" style="float: right;">✕ Fechar</button>
                    </div>
                    <div class="card-body">
                        <div id="detalhes-conteudo">
                            <!-- Conteúdo dinâmico -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Dados das lojas/VDs da planilha
        const lojasVD = [
            "ABRÃO TOMÉ_17612►52.087.749/0030-56",
            "AMIGAO MIRAGAIA_22375►51.769.304/0005-82",
            "AMIGAO_14252►52.087.749/0026-70",
            "ANDRADINA CENTRO_22405►51.769.304/0008-25",
            "ANDRADINA SHOP_22401►51.769.304/0009-06",
            "ARAÇATUBA_5037►52.087.749/0008-98",
            "AURIFLAMA_23525►51.769.304/0012-01",
            "BANDEIRANTES_22403►51.769.304/0004-00",
            "BARÃO_22404►51.769.304/0002-30",
            "CARREFOUR_12853►52.087.749/0022-46",
            "CASTILHO_22402►51.769.304/0010-40",
            "FARIA_4701►52.087.749/0003-83",
            "FERNANDOPOLIS_13019►52.087.749/0020-84",
            "GARDEN_4794►52.087.749/0006-26",
            "GENERAL SALGADO_23515►51.769.304/0011-20",
            "GENERAL_5036►52.087.749/0007-07",
            "GUAPIAÇU_14378►52.087.749/0027-50",
            "GUARARAPES_22374►51.769.304/0006-63",
            "IGUATEMI_17315►52.087.749/0028-31",
            "ILHA SOLTEIRA QUIOSQUE_23527►51.769.304/0013-92",
            "ILHA SOLTEIRA_23518►51.769.304/0019-88",
            "IMPERIAL_900346►52.087.749/0001-11",
            "JALES_13018►52.087.749/0019-40",
            "KMB-DISTRIBUIDORA_23663-57.951.960/0001-54",
            "MARANHÃO_13904►52.087.749/0024-08",
            "MINAS_4684►52.087.749/0005-45",
            "MIRANDÓPOLIS_22406►51.769.304/0007-44",
            "MIRASSOL_4685►52.087.749/0004-64",
            "MIRASSOLANDIA_11021►52.087.749/0009-79",
            "MUFFATO_14736►52.087.749/0029-12",
            "MULTISHOP_12524►52.087.749/0013-55",
            "NOVA GRANADA_13017►52.087.749/0017-89",
            "PALMEIRA D'OESTE_23526►51.769.304/0016-35",
            "PEREIRA BARRETO QUIOSQUE_23530►51.769.304/0014-73",
            "PEREIRA BARRETO_23514►51.769.304/0017-16",
            "PHILADELPHO_20385►52.087.749/0032-18",
            "PLAZA_12901►52.087.749/0015-17",
            "POTIRENDABA_13016►52.087.749/0016-06",
            "PRAÇA NOVA_18591►52.087.749/0031-37",
            "PRAÇA_6119►52.087.749/0010-02",
            "QDB - FARIA_10152►19.508.022/0001-95",
            "RONDON_13015►52.087.749/0018-60",
            "SANTA FÉ DO SUL QUIOSQUE_23529►51.769.304/0015-54",
            "Santa Fé do Sul_23505►51.769.304/0018-05",
            "SAUDADES_22373►51.769.304/0003-10",
            "SHOPPING NORTE_13922►52.087.749/0023-27",
            "TABAPUÃ_13123►52.087.749/0021-65",
            "TANABI_5783►52.087.749/0011-93",
            "VD ARAÇATUBA_22491►51.993.192/0001-15",
            "VD CATANDUVA_22511-52.539.781/0001-90",
            "VD FERNANDÓPOLIS_23528►52.556.662/0002-27",
            "VD JALES_22512-52.556.662/0001-46",
            "VD RIO PRETO_13372-14.180.298/0001-73",
            "WALMART_CATAN_14268-52.087.749/0025-99",
            "WALMART_RIO PRETO_12760-52.087.749/0014-36"
        ];

        // Sistema de usuários
        const usuarios = {
            solicitante: [
                { username: 'usuario', password: 'senha123', nome: 'Usuário Padrão' },
                { username: 'joao', password: '123456', nome: 'João Silva' },
                { username: 'maria', password: '123456', nome: 'Maria Santos' }
            ],
            admin: [
                { username: 'admin', password: 'admin123', nome: 'Administrador' },
                { username: 'luciana', password: 'cpk2024', nome: 'Luciana Oliveira' }
            ]
        };

        // Estado da aplicação
        let currentUser = null;
        let userType = 'solicitante';

        // Inicialização da página
        document.addEventListener('DOMContentLoaded', function() {
            inicializarLogin();
            inicializarSistema();
            verificarLogin();
        });

        // Sistema de Login
        function inicializarLogin() {
            // Seletor de tipo de usuário
            document.querySelectorAll('.user-type-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.user-type-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    userType = this.dataset.type;
                });
            });

            // Botão de login
            document.getElementById('btn-login').addEventListener('click', fazerLogin);

            // Enter para login
            document.getElementById('login-password').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') fazerLogin();
            });
        }

        function fazerLogin() {
            const username = document.getElementById('login-username').value.trim();
            const password = document.getElementById('login-password').value;

            if (!username || !password) {
                alert('Por favor, preencha usuário e senha.');
                return;
            }

            const userList = usuarios[userType];
            const user = userList.find(u => u.username === username && u.password === password);

            if (user) {
                currentUser = { ...user, type: userType };
                localStorage.setItem('currentUser', JSON.stringify(currentUser));
                mostrarSistema();
            } else {
                alert('Usuário ou senha incorretos!');
            }
        }

        function verificarLogin() {
            const savedUser = localStorage.getItem('currentUser');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                userType = currentUser.type;
                mostrarSistema();
            }
        }

        function logout() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            mostrarLogin();
        }

        function mostrarLogin() {
            document.getElementById('login-screen').classList.remove('hidden');
            document.getElementById('main-system').classList.add('hidden');
            document.getElementById('login-username').value = '';
            document.getElementById('login-password').value = '';
        }

        function mostrarSistema() {
            document.getElementById('login-screen').classList.add('hidden');
            document.getElementById('main-system').classList.remove('hidden');
            
            // Atualizar informações do usuário
            document.getElementById('current-user').textContent = currentUser.nome;
            
            const roleBadge = document.getElementById('user-role-badge');
            if (currentUser.type === 'admin') {
                roleBadge.innerHTML = '<span class="status-badge status-aprovado">Administrador</span>';
                document.getElementById('solicitante-area').classList.add('hidden');
                document.getElementById('admin-area').classList.remove('hidden');
                document.getElementById('historico-subtitle').textContent = 'Todas as requisições do sistema';
            } else {
                roleBadge.innerHTML = '<span class="status-badge status-pendente">Solicitante</span>';
                document.getElementById('solicitante-area').classList.remove('hidden');
                document.getElementById('admin-area').classList.add('hidden');
                document.getElementById('historico-subtitle').textContent = 'Suas requisições';
            }

            // Botão de logout
            document.getElementById('btn-logout').addEventListener('click', logout);

            // Inicializar sistema principal
            inicializarSistemaPrincipal();
        }

        // Sistema Principal
        function inicializarSistema() {
            // Preencher dropdown de lojas/VDs
            const selectLojaVD = document.getElementById('loja-vd');
            lojasVD.forEach(loja => {
                const option = document.createElement('option');
                option.value = loja;
                option.textContent = loja.split('►')[0];
                selectLojaVD.appendChild(option);
            });

            // Definir data atual
            const dataInput = document.getElementById('data');
            const hoje = new Date().toISOString().split('T')[0];
            dataInput.value = hoje;
        }

        function inicializarSistemaPrincipal() {
            // Botão adicionar item
            document.getElementById('btn-adicionar-item').addEventListener('click', adicionarItem);

            // Botão limpar
            document.getElementById('btn-limpar').addEventListener('click', limparFormulario);

            // Botão enviar
            document.getElementById('btn-enviar').addEventListener('click', enviarRequisicao);

            // Botão fechar modal
            document.getElementById('btn-fechar-modal').addEventListener('click', function() {
                document.getElementById('modal-detalhes').classList.add('hidden');
            });

            // Carregar histórico
            carregarHistorico();
        }

        function adicionarItem() {
            const container = document.getElementById('itens-container');
            const novoItem = document.createElement('div');
            novoItem.className = 'item-row';
            novoItem.innerHTML = `
                <div class="item-desc">
                    <input type="text" class="item-descricao" placeholder="Descrição do Material e/ou Produto" required>
                </div>
                <div class="item-qty">
                    <input type="number" class="item-quantidade" placeholder="Quantidade" min="1" required>
                </div>
                <div class="item-actions">
                    <button type="button" class="btn btn-danger btn-remover-item btn-sm">🗑️ Remover</button>
                </div>
            `;
            container.appendChild(novoItem);

            novoItem.querySelector('.btn-remover-item').addEventListener('click', function() {
                if (container.children.length > 1) {
                    container.removeChild(novoItem);
                } else {
                    alert('É necessário pelo menos um item na requisição.');
                }
            });
        }

        function limparFormulario() {
            if (confirm('Tem certeza que deseja limpar o formulário? Todos os dados não enviados serão perdidos.')) {
                document.getElementById('solicitante').value = currentUser.nome;
                document.getElementById('loja-vd').value = '';
                document.getElementById('voltagem').value = '';
                document.getElementById('link-foto').value = '';
                
                const container = document.getElementById('itens-container');
                while (container.children.length > 1) {
                    container.removeChild(container.lastChild);
                }
                
                container.querySelector('.item-descricao').value = '';
                container.querySelector('.item-quantidade').value = '';
                
                document.getElementById('solicitante').focus();
            }
        }

        function enviarRequisicao() {
            const solicitante = document.getElementById('solicitante').value.trim() || currentUser.nome;
            const data = document.getElementById('data').value;
            const lojaVD = document.getElementById('loja-vd').value;
            const voltagem = document.getElementById('voltagem').value;
            const linkFoto = document.getElementById('link-foto').value.trim();
            
            if (!solicitante || !data || !lojaVD) {
                alert('Por favor, preencha todos os campos obrigatórios: Solicitante, Data e Loja/VD.');
                return;
            }
            
            const itens = [];
            const itensRows = document.querySelectorAll('.item-row');
            let itensValidos = false;
            
            itensRows.forEach(row => {
                const descricao = row.querySelector('.item-descricao').value.trim();
                const quantidade = row.querySelector('.item-quantidade').value;
                
                if (descricao && quantidade) {
                    itens.push({ descricao, quantidade: parseInt(quantidade) });
                    itensValidos = true;
                }
            });
            
            if (!itensValidos) {
                alert('Por favor, adicione pelo menos um item válido com descrição e quantidade.');
                return;
            }
            
            const requisicao = {
                id: Date.now(),
                data,
                solicitante,
                lojaVD,
                voltagem: voltagem || 'Não informada',
                linkFoto: linkFoto || 'Não informado',
                itens,
                status: 'Pendente',
                dataEnvio: new Date().toLocaleString('pt-BR'),
                criadoPor: currentUser.username,
                observacoes: ''
            };
            
            salvarRequisicao(requisicao);
            carregarHistorico();
            limparFormulario();
            
            alert('✅ Requisição enviada com sucesso!\n\nSolicitante: ' + solicitante + 
                  '\nData: ' + new Date(data).toLocaleDateString('pt-BR') +
                  '\nItens: ' + itens.length + ' item(ns)');
        }

        function salvarRequisicao(requisicao) {
            let historico = JSON.parse(localStorage.getItem('historicoRequisicoes')) || [];
            historico.push(requisicao);
            localStorage.setItem('historicoRequisicoes', JSON.stringify(historico));
        }

        function carregarHistorico() {
            const historico = JSON.parse(localStorage.getItem('historicoRequisicoes')) || [];
            const tbody = document.querySelector('#tabela-historico tbody');
            tbody.innerHTML = '';
            
            if (historico.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="6">
                            <div class="empty-state">
                                <i>📝</i>
                                <p>Nenhuma requisição encontrada</p>
                                <small>As requisições aparecerão aqui após o envio</small>
                            </div>
                        </td>
                    </tr>
                `;
                return;
            }
            
            // Filtrar por usuário se for solicitante
            let historicoFiltrado = historico;
            if (currentUser.type === 'solicitante') {
                historicoFiltrado = historico.filter(req => req.criadoPor === currentUser.username);
            }
            
            // Ordenar por data (mais recente primeiro)
            historicoFiltrado.sort((a, b) => new Date(b.data) - new Date(a.data));
            
            historicoFiltrado.forEach(req => {
                const tr = document.createElement('tr');
                
                const dataObj = new Date(req.data);
                const dataFormatada = dataObj.toLocaleDateString('pt-BR');
                
                const itensResumo = req.itens.length > 0 
                    ? `${req.itens[0].descricao.substring(0, 25)}${req.itens[0].descricao.length > 25 ? '...' : ''} (+${req.itens.length - 1} ${req.itens.length - 1 === 1 ? 'item' : 'itens'})` 
                    : 'Sem itens';
                
                const statusClass = `status-${req.status.toLowerCase()}`;
                
                tr.innerHTML = `
                    <td>${dataFormatada}</td>
                    <td><strong>${req.solicitante}</strong></td>
                    <td>${req.lojaVD.split('►')[0]}</td>
                    <td>${itensResumo}</td>
                    <td><span class="status-badge ${statusClass}">${req.status}</span></td>
                    <td>
                        <button type="button" class="btn btn-primary btn-sm btn-ver-detalhes" data-id="${req.id}">
                            👁️ Ver Detalhes
                        </button>
                    </td>
                `;
                
                tbody.appendChild(tr);
            });

            // Adicionar eventos aos botões de detalhes
            document.querySelectorAll('.btn-ver-detalhes').forEach(btn => {
                btn.addEventListener('click', function() {
                    const reqId = parseInt(this.dataset.id);
                    mostrarDetalhesRequisicao(reqId);
                });
            });
        }

        function mostrarDetalhesRequisicao(reqId) {
            const historico = JSON.parse(localStorage.getItem('historicoRequisicoes')) || [];
            const requisicao = historico.find(req => req.id === reqId);
            
            if (!requisicao) {
                alert('Requisição não encontrada!');
                return;
            }
            
            const detalhesHTML = `
                <div class="requisicao-detalhes">
                    <div class="form-row">
                        <div class="form-col">
                            <strong>👤 Solicitante:</strong> ${requisicao.solicitante}
                        </div>
                        <div class="form-col">
                            <strong>📅 Data:</strong> ${new Date(requisicao.data).toLocaleDateString('pt-BR')}
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-col">
                            <strong>🏪 Loja/VD:</strong> ${requisicao.lojaVD}
                        </div>
                        <div class="form-col">
                            <strong>⚡ Voltagem:</strong> ${requisicao.voltagem}
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-col">
                            <strong>🔗 Link/Foto:</strong> ${requisicao.linkFoto}
                        </div>
                        <div class="form-col">
                            <strong>📋 Status:</strong> 
                            <span class="status-badge status-${requisicao.status.toLowerCase()}">
                                ${requisicao.status}
                            </span>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <strong>🛍️ Itens Solicitados:</strong>
                        <table>
                            <thead>
                                <tr>
                                    <th>Item</th>
                                    <th>Descrição</th>
                                    <th>Quantidade</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${requisicao.itens.map((item, index) => `
                                    <tr>
                                        <td>${index + 1}</td>
                                        <td>${item.descricao}</td>
                                        <td>${item.quantidade}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                    </div>
                    
                    ${currentUser.type === 'admin' ? `
                        <div class="admin-actions">
                            <strong>Alterar Status:</strong>
                            <button type="button" class="btn btn-success btn-sm btn-alterar-status" data-id="${requisicao.id}" data-status="Aprovado">
                                ✅ Aprovar
                            </button>
                            <button type="button" class="btn btn-danger btn-sm btn-alterar-status" data-id="${requisicao.id}" data-status="Rejeitado">
                                ❌ Rejeitar
                            </button>
                            <button type="button" class="btn btn-warning btn-sm btn-alterar-status" data-id="${requisicao.id}" data-status="Pendente">
                                ⏳ Pendente
                            </button>
                            <button type="button" class="btn btn-primary btn-sm btn-alterar-status" data-id="${requisicao.id}" data-status="Finalizado">
                                🏁 Finalizar
                            </button>
                        </div>
                        
                        <div class="form-group">
                            <label for="observacoes-${requisicao.id}">Observações:</label>
                            <textarea id="observacoes-${requisicao.id}" placeholder="Adicione observações sobre esta requisição" style="width: 100%; height: 80px;">${requisicao.observacoes || ''}</textarea>
                            <button type="button" class="btn btn-primary btn-sm" onclick="salvarObservacoes(${requisicao.id})" style="margin-top: 10px;">
                                💾 Salvar Observações
                            </button>
                        </div>
                    ` : ''}
                    
                    ${requisicao.observacoes ? `
                        <div class="form-group">
                            <strong>📝 Observações:</strong>
                            <div style="padding: 10px; background: #f8f9fa; border-radius: 6px; margin-top: 5px;">
                                ${requisicao.observacoes}
                            </div>
                        </div>
                    ` : ''}
                </div>
            `;
            
            document.getElementById('detalhes-conteudo').innerHTML = detalhesHTML;
            document.getElementById('modal-detalhes').classList.remove('hidden');
            
            // Adicionar eventos aos botões de alterar status
            if (currentUser.type === 'admin') {
                document.querySelectorAll('.btn-alterar-status').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const reqId = parseInt(this.dataset.id);
                        const novoStatus = this.dataset.status;
                        alterarStatusRequisicao(reqId, novoStatus);
                    });
                });
            }
        }

        function alterarStatusRequisicao(reqId, novoStatus) {
            const historico = JSON.parse(localStorage.getItem('historicoRequisicoes')) || [];
            const requisicaoIndex = historico.findIndex(req => req.id === reqId);
            
            if (requisicaoIndex !== -1) {
                historico[requisicaoIndex].status = novoStatus;
                historico[requisicaoIndex].dataAtualizacao = new Date().toLocaleString('pt-BR');
                historico[requisicaoIndex].atualizadoPor = currentUser.nome;
                
                localStorage.setItem('historicoRequisicoes', JSON.stringify(historico));
                
                alert(`Status alterado para: ${novoStatus}`);
                carregarHistorico();
                mostrarDetalhesRequisicao(reqId); // Atualizar modal
            }
        }

        function salvarObservacoes(reqId) {
            const observacoes = document.getElementById(`observacoes-${reqId}`).value;
            const historico = JSON.parse(localStorage.getItem('historicoRequisicoes')) || [];
            const requisicaoIndex = historico.findIndex(req => req.id === reqId);
            
            if (requisicaoIndex !== -1) {
                historico[requisicaoIndex].observacoes = observacoes;
                localStorage.setItem('historicoRequisicoes', JSON.stringify(historico));
                alert('Observações salvas com sucesso!');
            }
        }

        // Preencher nome do solicitante automaticamente
        document.getElementById('solicitante').value = currentUser ? currentUser.nome : '';
    </script>
</body>
</html>
