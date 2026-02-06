<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FR9STZN | Sistema de Chaves</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #00ff88;
            --primary-dark: #00cc6a;
            --secondary: #1a1a2e;
            --dark: #0f1419;
            --darker: #0a0e12;
            --light: #f0f0f0;
            --gray: #2d3748;
            --danger: #ff4757;
            --warning: #ffa502;
            --info: #2ed573;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--darker), var(--secondary));
            color: var(--light);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 500px;
            background: rgba(15, 20, 25, 0.95);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(0, 255, 136, 0.1);
            backdrop-filter: blur(10px);
        }
        
        .logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .logo h1 {
            font-size: 2.5rem;
            font-weight: 900;
            background: linear-gradient(to right, var(--primary), #00ffcc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 10px;
        }
        
        .logo p {
            color: #aaa;
            font-size: 1rem;
        }
        
        /* Forms */
        .form-container {
            display: none;
        }
        
        .form-container.active {
            display: block;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .form-title {
            font-size: 1.5rem;
            color: var(--primary);
            margin-bottom: 25px;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .input-group {
            margin-bottom: 25px;
        }
        
        .input-group label {
            display: block;
            margin-bottom: 8px;
            color: #ddd;
            font-weight: 500;
        }
        
        .input-with-icon {
            position: relative;
        }
        
        .input-with-icon i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--primary);
        }
        
        input[type="text"],
        input[type="password"] {
            width: 100%;
            padding: 15px 15px 15px 45px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            color: var(--light);
            font-size: 1rem;
            transition: all 0.3s;
        }
        
        input[type="text"]:focus,
        input[type="password"]:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 15px rgba(0, 255, 136, 0.2);
            background: rgba(255, 255, 255, 0.08);
        }
        
        .btn {
            width: 100%;
            padding: 16px;
            background: linear-gradient(45deg, var(--primary), var(--primary-dark));
            color: var(--darker);
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 255, 136, 0.3);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: var(--light);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.15);
            border-color: var(--primary);
        }
        
        /* Key Display */
        .key-display {
            background: rgba(0, 255, 136, 0.05);
            border: 2px solid rgba(0, 255, 136, 0.2);
            border-radius: 12px;
            padding: 20px;
            margin: 25px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .key-display::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--primary), #00ffcc, var(--primary));
            animation: shine 2s infinite linear;
        }
        
        @keyframes shine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        .key-label {
            color: #aaa;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }
        
        .key-value {
            font-family: 'Courier New', monospace;
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--primary);
            letter-spacing: 2px;
            word-break: break-all;
            padding: 10px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 8px;
            margin: 10px 0;
            user-select: all;
        }
        
        /* Device Info */
        .device-info {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 12px;
            padding: 20px;
            margin: 25px 0;
        }
        
        .device-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        .device-item:last-child {
            border-bottom: none;
        }
        
        .device-label {
            color: #aaa;
        }
        
        .device-value {
            color: var(--primary);
            font-weight: 600;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 12px;
            padding: 5px;
            margin-bottom: 30px;
        }
        
        .tab {
            flex: 1;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            border-radius: 8px;
            transition: all 0.3s;
            font-weight: 600;
            color: #aaa;
        }
        
        .tab.active {
            background: linear-gradient(45deg, var(--primary), var(--primary-dark));
            color: var(--darker);
        }
        
        /* Message Box */
        .message-box {
            padding: 15px;
            border-radius: 12px;
            margin: 20px 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .message-box.success {
            background: rgba(46, 213, 115, 0.1);
            border-left: 4px solid var(--info);
            color: #2ed573;
        }
        
        .message-box.error {
            background: rgba(255, 71, 87, 0.1);
            border-left: 4px solid var(--danger);
            color: #ff9999;
        }
        
        .message-box.info {
            background: rgba(255, 165, 2, 0.1);
            border-left: 4px solid var(--warning);
            color: #ffa502;
        }
        
        /* Admin Panel */
        .admin-panel {
            display: none;
        }
        
        .admin-panel.active {
            display: block;
        }
        
        .key-list {
            max-height: 300px;
            overflow-y: auto;
            margin: 20px 0;
        }
        
        .key-item {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 10px;
            border-left: 4px solid var(--primary);
        }
        
        .key-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        
        .key-code {
            font-family: 'Courier New', monospace;
            font-weight: 600;
            color: var(--primary);
        }
        
        .key-status {
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        
        .key-status.active {
            background: rgba(46, 213, 115, 0.2);
            color: #2ed573;
        }
        
        .key-status.limited {
            background: rgba(255, 165, 2, 0.2);
            color: #ffa502;
        }
        
        .key-status.blocked {
            background: rgba(255, 71, 87, 0.2);
            color: #ff9999;
        }
        
        .key-details {
            font-size: 0.9rem;
            color: #aaa;
        }
        
        /* Footer */
        .footer {
            text-align: center;
            margin-top: 30px;
            color: #777;
            font-size: 0.9rem;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        /* Copy Button */
        .copy-btn {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            color: var(--light);
            padding: 8px 15px;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 0.9rem;
            transition: all 0.3s;
        }
        
        .copy-btn:hover {
            background: rgba(0, 255, 136, 0.2);
            color: var(--primary);
        }
        
        /* Responsive */
        @media (max-width: 600px) {
            .container {
                padding: 30px 20px;
            }
            
            .logo h1 {
                font-size: 2rem;
            }
            
            .key-value {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo">
            <h1>FR9STZN KEY SYSTEM</h1>
            <p>Sistema de acesso ao Gerador de Sensibilidade</p>
        </div>
        
        <!-- Tabs Navigation -->
        <div class="tabs">
            <div class="tab active" data-tab="login">ACESSAR</div>
            <div class="tab" data-tab="generate">GERAR CHAVE</div>
            <div class="tab" data-tab="admin">ADMIN</div>
        </div>
        
        <!-- Message Box -->
        <div id="messageBox" class="message-box" style="display: none;"></div>
        
        <!-- Login Form -->
        <div id="loginForm" class="form-container active">
            <h2 class="form-title"><i class="fas fa-key"></i> Digite sua Chave de Acesso</h2>
            
            <div class="input-group">
                <label for="userKey">Chave de Licença:</label>
                <div class="input-with-icon">
                    <i class="fas fa-key"></i>
                    <input type="text" id="userKey" placeholder="XXXX-XXXX-XXXX-XXXX" maxlength="19">
                </div>
            </div>
            
            <button class="btn" id="loginBtn">
                <i class="fas fa-sign-in-alt"></i> ACESSAR GERADOR
            </button>
            
            <div class="device-info">
                <div class="device-item">
                    <span class="device-label">Dispositivo Atual:</span>
                    <span class="device-value" id="currentDevice">-</span>
                </div>
                <div class="device-item">
                    <span class="device-label">Chave Ativa:</span>
                    <span class="device-value" id="activeKeyStatus">Não</span>
                </div>
                <div class="device-item">
                    <span class="device-label">Dispositivos Usados:</span>
                    <span class="device-value" id="usedDevices">0/2</span>
                </div>
            </div>
        </div>
        
        <!-- Generate Key Form -->
        <div id="generateForm" class="form-container">
            <h2 class="form-title"><i class="fas fa-plus-circle"></i> Gerar Nova Chave</h2>
            
            <div class="input-group">
                <label for="adminPassword">Senha de Administrador:</label>
                <div class="input-with-icon">
                    <i class="fas fa-lock"></i>
                    <input type="password" id="adminPassword" placeholder="Digite a senha de admin">
                </div>
            </div>
            
            <button class="btn" id="generateKeyBtn">
                <i class="fas fa-bolt"></i> GERAR CHAVE PERMANENTE
            </button>
            
            <div class="key-display" style="display: none;" id="generatedKeyContainer">
                <div class="key-label">CHAVE GERADA COM SUCESSO</div>
                <div class="key-value" id="generatedKey">XXXX-XXXX-XXXX-XXXX</div>
                <div class="key-label">Esta chave pode ser usada em 2 dispositivos diferentes</div>
                <button class="copy-btn" id="copyKeyBtn">
                    <i class="far fa-copy"></i> COPIAR CHAVE
                </button>
            </div>
        </div>
        
        <!-- Admin Panel -->
        <div id="adminPanel" class="form-container admin-panel">
            <h2 class="form-title"><i class="fas fa-user-shield"></i> Painel de Administração</h2>
            
            <div class="input-group">
                <label for="adminLoginPassword">Senha de Administrador:</label>
                <div class="input-with-icon">
                    <i class="fas fa-lock"></i>
                    <input type="password" id="adminLoginPassword" placeholder="Digite a senha de admin">
                </div>
            </div>
            
            <button class="btn" id="adminLoginBtn">
                <i class="fas fa-sign-in-alt"></i> ACESSAR PAINEL
            </button>
            
            <div id="adminContent" style="display: none;">
                <h3 style="margin: 25px 0 15px 0; color: var(--primary);">Chaves Geradas</h3>
                
                <div class="key-list" id="keyList">
                    <!-- Keys will be loaded here -->
                </div>
                
                <div class="input-group">
                    <label for="searchKey">Buscar Chave:</label>
                    <div class="input-with-icon">
                        <i class="fas fa-search"></i>
                        <input type="text" id="searchKey" placeholder="Digite parte da chave">
                    </div>
                </div>
                
                <button class="btn btn-secondary" id="refreshKeysBtn">
                    <i class="fas fa-sync-alt"></i> ATUALIZAR LISTA
                </button>
                
                <button class="btn btn-secondary" id="exportKeysBtn" style="margin-top: 10px;">
                    <i class="fas fa-download"></i> EXPORTAR CHAVES
                </button>
            </div>
        </div>
        
        <div class="footer">
            <p>FR9STZN Key System &copy; 2024</p>
            <p style="font-size: 0.8rem; margin-top: 5px; color: #666;">
                Cada chave permite acesso em até 2 dispositivos diferentes
            </p>
        </div>
    </div>

    <script>
        // Configuration
        const CONFIG = {
            ADMIN_PASSWORD: "ADMINSGENERATOR1408", // Change this to your desired password
            MAX_DEVICES_PER_KEY: 2,
            KEY_FORMAT: "XXXX-XXXX-XXXX-XXXX"
        };

        // State
        let currentTab = 'login';
        let generatedKeys = JSON.parse(localStorage.getItem('fr9stzn_keys') || '[]');
        let usedDevices = JSON.parse(localStorage.getItem('fr9stzn_devices') || '{}');
        let currentDeviceId = null;

        // Generate device fingerprint
        function generateDeviceId() {
            const userAgent = navigator.userAgent;
            const screen = window.screen;
            const timezone = Intl.DateTimeFormat().resolvedOptions().timeZone;
            
            const components = [
                userAgent,
                screen.width,
                screen.height,
                screen.colorDepth,
                timezone,
                navigator.language,
                navigator.hardwareConcurrency || 'unknown'
            ];
            
            // Simple hash function
            let hash = 0;
            const str = components.join('|');
            for (let i = 0; i < str.length; i++) {
                hash = ((hash << 5) - hash) + str.charCodeAt(i);
                hash = hash & hash;
            }
            
            return 'DEV-' + Math.abs(hash).toString(36).substring(0, 8).toUpperCase();
        }

        // Generate a random key
        function generateRandomKey() {
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            let key = '';
            
            for (let i = 0; i < 16; i++) {
                if (i > 0 && i % 4 === 0) key += '-';
                key += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            
            return key;
        }

        // Format key for display
        function formatKey(key) {
            return key.replace(/(.{4})/g, '$1-').slice(0, -1);
        }

        // Show message
        function showMessage(message, type = 'info') {
            const box = document.getElementById('messageBox');
            box.className = `message-box ${type}`;
            box.innerHTML = `<i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : 'info-circle'}"></i> ${message}`;
            box.style.display = 'flex';
            
            if (type === 'success') {
                setTimeout(() => {
                    box.style.display = 'none';
                }, 5000);
            }
        }

        // Save keys to localStorage
        function saveKeys() {
            localStorage.setItem('fr9stzn_keys', JSON.stringify(generatedKeys));
            localStorage.setItem('fr9stzn_devices', JSON.stringify(usedDevices));
        }

        // Check if key is valid
        function isValidKey(key) {
            return generatedKeys.some(k => k.key === key && k.active);
        }

        // Check device usage for a key
        function checkDeviceUsage(key) {
            if (!usedDevices[key]) {
                usedDevices[key] = [];
            }
            
            currentDeviceId = generateDeviceId();
            
            // Check if device is already registered
            if (usedDevices[key].includes(currentDeviceId)) {
                return true; // Device already using this key
            }
            
            // Check if key has reached device limit
            if (usedDevices[key].length >= CONFIG.MAX_DEVICES_PER_KEY) {
                return false; // Key limit reached
            }
            
            // Register new device
            usedDevices[key].push(currentDeviceId);
            saveKeys();
            return true;
        }

        // Get key info
        function getKeyInfo(key) {
            return generatedKeys.find(k => k.key === key);
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            // Generate current device ID
            currentDeviceId = generateDeviceId();
            document.getElementById('currentDevice').textContent = currentDeviceId.substring(0, 12) + '...';
            
            // Tab switching
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    
                    // Update tabs
                    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Update forms
                    document.querySelectorAll('.form-container').forEach(form => {
                        form.classList.remove('active');
                    });
                    
                    if (tabId === 'login') {
                        document.getElementById('loginForm').classList.add('active');
                    } else if (tabId === 'generate') {
                        document.getElementById('generateForm').classList.add('active');
                    } else if (tabId === 'admin') {
                        document.getElementById('adminPanel').classList.add('active');
                    }
                    
                    currentTab = tabId;
                    document.getElementById('messageBox').style.display = 'none';
                });
            });
            
            // Login button
            document.getElementById('loginBtn').addEventListener('click', function() {
                const keyInput = document.getElementById('userKey').value.trim().toUpperCase();
                const cleanKey = keyInput.replace(/-/g, '');
                
                if (!cleanKey || cleanKey.length !== 16) {
                    showMessage('Por favor, digite uma chave válida no formato XXXX-XXXX-XXXX-XXXX', 'error');
                    return;
                }
                
                const formattedKey = formatKey(cleanKey);
                
                if (!isValidKey(formattedKey)) {
                    showMessage('Chave inválida ou expirada. Verifique e tente novamente.', 'error');
                    return;
                }
                
                if (!checkDeviceUsage(formattedKey)) {
                    showMessage(`Esta chave já foi usada em ${CONFIG.MAX_DEVICES_PER_KEY} dispositivos diferentes. Limite atingido.`, 'error');
                    return;
                }
                
                // Update device info
                const keyInfo = getKeyInfo(formattedKey);
                const deviceCount = usedDevices[formattedKey] ? usedDevices[formattedKey].length : 0;
                
                document.getElementById('activeKeyStatus').textContent = 'Sim';
                document.getElementById('usedDevices').textContent = `${deviceCount}/${CONFIG.MAX_DEVICES_PER_KEY}`;
                
                showMessage('Chave válida! Redirecionando para o gerador de sensibilidade...', 'success');
                
                // Store access in session
                sessionStorage.setItem('fr9stzn_access', formattedKey);
                sessionStorage.setItem('fr9stzn_device', currentDeviceId);
                
                // Redirect to sensitivity calculator after delay
                setTimeout(() => {
                    window.location.href = 'sensitivity_calculator.html'; // Change to your actual page
                }, 2000);
            });
            
            // Generate key button
            document.getElementById('generateKeyBtn').addEventListener('click', function() {
                const password = document.getElementById('adminPassword').value;
                
                if (password !== CONFIG.ADMIN_PASSWORD) {
                    showMessage('Senha de administrador incorreta.', 'error');
                    return;
                }
                
                const newKey = generateRandomKey();
                const formattedKey = formatKey(newKey);
                
                // Add to keys list
                generatedKeys.push({
                    key: formattedKey,
                    created: new Date().toISOString(),
                    active: true,
                    devices: 0
                });
                
                saveKeys();
                
                // Show generated key
                document.getElementById('generatedKey').textContent = formattedKey;
                document.getElementById('generatedKeyContainer').style.display = 'block';
                
                showMessage('Chave gerada com sucesso!', 'success');
                document.getElementById('adminPassword').value = '';
            });
            
            // Copy key button
            document.getElementById('copyKeyBtn').addEventListener('click', function() {
                const keyText = document.getElementById('generatedKey').textContent;
                navigator.clipboard.writeText(keyText).then(() => {
                    const originalHTML = this.innerHTML;
                    this.innerHTML = '<i class="fas fa-check"></i> CHAVE COPIADA!';
                    this.style.background = 'rgba(46, 213, 115, 0.3)';
                    
                    setTimeout(() => {
                        this.innerHTML = originalHTML;
                        this.style.background = '';
                    }, 2000);
                });
            });
            
            // Admin login button
            document.getElementById('adminLoginBtn').addEventListener('click', function() {
                const password = document.getElementById('adminLoginPassword').value;
                
                if (password !== CONFIG.ADMIN_PASSWORD) {
                    showMessage('Senha de administrador incorreta.', 'error');
                    return;
                }
                
                document.getElementById('adminContent').style.display = 'block';
                loadKeyList();
                showMessage('Painel de administração acessado com sucesso.', 'success');
            });
            
            // Refresh keys button
            document.getElementById('refreshKeysBtn').addEventListener('click', loadKeyList);
            
            // Search key input
            document.getElementById('searchKey').addEventListener('input', function() {
                loadKeyList(this.value);
            });
            
            // Export keys button
            document.getElementById('exportKeysBtn').addEventListener('click', function() {
                exportKeysToCSV();
            });
            
            // Auto-format key input
            document.getElementById('userKey').addEventListener('input', function(e) {
                let value = e.target.value.toUpperCase().replace(/[^A-Z0-9]/g, '');
                
                if (value.length > 16) {
                    value = value.substring(0, 16);
                }
                
                // Add dashes
                let formatted = '';
                for (let i = 0; i < value.length; i++) {
                    if (i > 0 && i % 4 === 0) {
                        formatted += '-';
                    }
                    formatted += value[i];
                }
                
                e.target.value = formatted;
            });
        });
        
        // Load key list for admin
        function loadKeyList(filter = '') {
            const keyList = document.getElementById('keyList');
            keyList.innerHTML = '';
            
            let filteredKeys = generatedKeys;
            
            if (filter) {
                filteredKeys = generatedKeys.filter(k => 
                    k.key.toLowerCase().includes(filter.toLowerCase())
                );
            }
            
            if (filteredKeys.length === 0) {
                keyList.innerHTML = '<div style="text-align: center; color: #666; padding: 20px;">Nenhuma chave encontrada</div>';
                return;
            }
            
            filteredKeys.forEach(keyData => {
                const deviceCount = usedDevices[keyData.key] ? usedDevices[keyData.key].length : 0;
                const maxDevices = CONFIG.MAX_DEVICES_PER_KEY;
                const status = deviceCount >= maxDevices ? 'limited' : keyData.active ? 'active' : 'blocked';
                const statusText = deviceCount >= maxDevices ? 'LIMITADO' : keyData.active ? 'ATIVO' : 'BLOQUEADO';
                
                const keyItem = document.createElement('div');
                keyItem.className = 'key-item';
                keyItem.innerHTML = `
                    <div class="key-header">
                        <span class="key-code">${keyData.key}</span>
                        <span class="key-status ${status}">${statusText}</span>
                    </div>
                    <div class="key-details">
                        <div>Criada: ${new Date(keyData.created).toLocaleDateString('pt-BR')}</div>
                        <div>Dispositivos: ${deviceCount}/${maxDevices}</div>
                        <div>Status: ${keyData.active ? 'Ativa' : 'Inativa'}</div>
                    </div>
                `;
                
                keyList.appendChild(keyItem);
            });
        }
        
        // Export keys to CSV
        function exportKeysToCSV() {
            let csv = 'Chave,Data de Criação,Status,Dispositivos Usados\n';
            
            generatedKeys.forEach(keyData => {
                const deviceCount = usedDevices[keyData.key] ? usedDevices[keyData.key].length : 0;
                csv += `"${keyData.key}","${new Date(keyData.created).toLocaleDateString('pt-BR')}","${keyData.active ? 'Ativa' : 'Inativa'}","${deviceCount}/${CONFIG.MAX_DEVICES_PER_KEY}"\n`;
            });
            
            const blob = new Blob([csv], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `fr9stzn_keys_${new Date().toISOString().split('T')[0]}.csv`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            
            showMessage('Lista de chaves exportada com sucesso!', 'success');
        }
        
        // Check for existing access on page load
        function checkExistingAccess() {
            const savedKey = sessionStorage.getItem('fr9stzn_access');
            const savedDevice = sessionStorage.getItem('fr9stzn_device');
            
            if (savedKey && savedDevice === currentDeviceId) {
                const deviceCount = usedDevices[savedKey] ? usedDevices[savedKey].length : 0;
                
                document.getElementById('userKey').value = savedKey;
                document.getElementById('activeKeyStatus').textContent = 'Sim';
                document.getElementById('usedDevices').textContent = `${deviceCount}/${CONFIG.MAX_DEVICES_PER_KEY}`;
                
                showMessage('Acesso anterior detectado. Você já pode acessar o gerador.', 'info');
            }
        }
        
        // Initialize access check
        checkExistingAccess();
        
        // Save initial keys if none exist (for demo)
        if (generatedKeys.length === 0) {
            // Create some demo keys
            const demoKeys = [
                {
                    key: formatKey('FR9STZN2024DEMO01'),
                    created: new Date().toISOString(),
                    active: true,
                    devices: 0
                },
                {
                    key: formatKey('TESTKEY000000001'),
                    created: new Date(Date.now() - 7 * 24 * 60 * 60 * 1000).toISOString(),
                    active: true,
                    devices: 1
                }
            ];
            
            generatedKeys.push(...demoKeys);
            saveKeys();
        }
    </script>
</body>
</html>
