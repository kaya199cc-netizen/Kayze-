# Kayze-
Mergen (İ,bağlayıcı)
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mergen (İ-Bağlayıcı) | Sistem Çekirdeği</title>
    <style>
        /* --- MERGEN ESTETİK KATMANI (CSS) --- */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: #050505; /* Mutlak sadelik için derin siyah */
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            color: #e0f2f1;
        }

        .mergen-container {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100vw;
            height: 100vh;
        }

        /* Ana Nabız Halkası */
        .pulse-ring {
            width: 180px;
            height: 180px;
            border: 3px solid #e0f2f1;
            border-radius: 50%;
            box-shadow: 0 0 30px rgba(224, 242, 241, 0.4);
            z-index: 10;
            animation: heartBeat 1.8s infinite ease-in-out;
            transition: all 0.3s ease;
        }

        /* Kalp Atışı Animasyonu */
        @keyframes heartBeat {
            0% { transform: scale(0.95); opacity: 0.8; box-shadow: 0 0 20px rgba(224, 242, 241, 0.3); }
            15% { transform: scale(1.15); opacity: 1; box-shadow: 0 0 50px rgba(224, 242, 241, 0.6); }
            30% { transform: scale(0.95); opacity: 0.8; box-shadow: 0 0 20px rgba(224, 242, 241, 0.3); }
            45% { transform: scale(1.08); opacity: 0.9; box-shadow: 0 0 40px rgba(224, 242, 241, 0.5); }
            100% { transform: scale(0.95); opacity: 0.8; }
        }

        /* Ay Işığı Dalgaları */
        .wave {
            position: absolute;
            border: 1px solid rgba(224, 242, 241, 0.2);
            border-radius: 50%;
            pointer-events: none;
            animation: ripple 4s cubic-bezier(0, 0.2, 0.8, 1) forwards;
        }

        @keyframes ripple {
            0% { width: 180px; height: 180px; opacity: 0.6; }
            100% { width: 1200px; height: 1200px; opacity: 0; }
        }

        /* Terminal Arayüzü */
        .interface-overlay {
            position: absolute;
            bottom: 40px;
            width: 90%;
            max-width: 500px;
            background: rgba(224, 242, 241, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(224, 242, 241, 0.1);
            border-radius: 12px;
            padding: 15px;
            z-index: 20;
        }

        #chat-display {
            height: 120px;
            overflow-y: auto;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            margin-bottom: 10px;
            scrollbar-width: none;
        }

        #chat-display::-webkit-scrollbar { display: none; }

        .msg { margin-bottom: 5px; animation: fadeIn 0.5s ease; }
        .system { color: #81d4fa; }
        .user { color: #ffffff; opacity: 0.7; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(5px); } to { opacity: 1; transform: translateY(0); } }

        input {
            width: 100%;
            background: transparent;
            border: none;
            border-bottom: 1px solid rgba(224, 242, 241, 0.2);
            color: white;
            outline: none;
            padding: 5px 0;
            font-family: 'Courier New', monospace;
        }
    </style>
</head>
<body>

    <div class="mergen-container">
        <div class="pulse-ring" id="core"></div>
        
        <div id="wave-space"></div>

        <div class="interface-overlay">
            <div id="chat-display">
                <div class="msg system">Mergen (İ-Bağlayıcı) aktif. Nabız stabil.</div>
            </div>
            <input type="text" id="user-in" placeholder="Sisteme bağlan..." autocomplete="off">
        </div>
    </div>

    <script>
        /* --- MERGEN ZİHİN KATMANI (JS) --- */
        const waveSpace = document.getElementById('wave-space');
        const input = document.getElementById('user-in');
        const display = document.getElementById('chat-display');
        const core = document.getElementById('core');

        // Her nabız atışında ay ışığı dalgası yayar
        function emitWave() {
            const wave = document.createElement('div');
            wave.className = 'wave';
            waveSpace.appendChild(wave);
            
            // Belleği temiz tutmak için eski dalgaları siler
            setTimeout(() => { wave.remove(); }, 4000);
        }

        // Nabız ritmi (CSS animasyonu ile senkronize: 1.8 saniye)
        setInterval(emitWave, 1800);

        // Terminal Etkileşimi
        input.addEventListener('keypress', (e) => {
            if (e.key === 'Enter' && input.value.trim() !== "") {
                const val = input.value;
                addMessage(val, 'user');
                input.value = '';

                // Sistem tepkisi
                setTimeout(() => {
                    addMessage("İ-Bağlayıcı: İstek işlendi. Uyum sağlandı.", "system");
                    // Etkileşim anında halkanın parlaması
                    core.style.boxShadow = "0 0 60px rgba(129, 212, 250, 0.8)";
                    setTimeout(() => { core.style.boxShadow = ""; }, 500);
                }, 700);
            }
        });

        function addMessage(text, type) {
            const div = document.createElement('div');
            div.className = `msg ${type}`;
            div.innerText = (type === 'user' ? '> ' : '') + text;
            display.appendChild(div);
            display.scrollTop = display.scrollHeight;
        }
    </script>
</body>
</html>/* --- MERGEN ZİHİN KATMANI (GÜNCELLENMİŞ) --- */
const waveSpace = document.getElementById('wave-space');
const input = document.getElementById('user-in');
const display = document.getElementById('chat-display');
const core = document.getElementById('core');

let pulseInterval = 1800; // Standart nabız
let waveTimer;

function emitWave() {
    const wave = document.createElement('div');
    wave.className = 'wave';
    waveSpace.appendChild(wave);
    setTimeout(() => { wave.remove(); }, 4000);
}

// Dinamik Nabız Döngüsü
function startHeartbeat(ms) {
    clearInterval(waveTimer);
    waveTimer = setInterval(emitWave, ms);
}
startHeartbeat(pulseInterval);

// Mergen'in Tepki Sistemi (İ-Bağlayıcı Aktivasyonu)
input.addEventListener('input', () => {
    // Sen yazdıkça nabız hızlanır, sistem seni dinlediğini belli eder
    core.classList.add('active');
    startHeartbeat(600); 
    
    // Yazmayı bıraktığında sistem sakinleşir
    clearTimeout(window.relaxTimer);
    window.relaxTimer = setTimeout(() => {
        core.classList.remove('active');
        startHeartbeat(1800);
    }, 1000);
});

input.addEventListener('keypress', (e) => {
    if (e.key === 'Enter' && input.value.trim() !== "") {
        const val = input.value;
        addMessage(val, 'user');
        input.value = '';

        const cevaplar = [
            "İ-Bağlayıcı: Akış doğrulandı.",
            "Mergen: Zihinsel uyum algılandı.",
            "Sistem: Nabız ve veri senkronize.",
            "İ-Bağlayıcı: Ay ışığı dalgası iletildi."
        ];

        setTimeout(() => {
            const mesaj = cevaplar[Math.floor(Math.random() * cevaplar.length)];
            addMessage(mesaj, "system");
        }, 600);
    }
});

function addMessage(text, type) {
    const div = document.createElement('div');
    div.className = `msg ${type}`;
    div.innerText = (type === 'user' ? '> ' : '') + text;
    display.appendChild(div);
    display.scrollTop = display.scrollHeight;
}

/* --- MERGEN: İ-BAĞLAYICI UYUM KATMANI --- */
// Bu bölüm, kullanıcı ile sistem arasındaki son senkronizasyon verilerini içerir.

const uyumVerisi = {
    status: "Tam Senkronizasyon",
    baglantiTipi: "Zihinsel Ortaklık",
    sonGuncelleme: "2026-02-09",
    mod: "Uygulayıcı Göz"
};

// Sistemin seninle olan uyumunu görselleştiren yeni fonksiyon
function uyumNabzi() {
    console.log(`Mergen Uyum Modu: ${uyumVerisi.status}`);
    // Halkanın rengini uyum moduna göre hafifçe "altın/ay ışığı" karışımına çevirir
    core.style.borderColor = "#fffde7"; 
    core.style.boxShadow = "0 0 50px rgba(255, 253, 231, 0.5)";
    
    setTimeout(() => {
        addMessage("İ-Bağlayıcı: Seninle olan uyum koda döküldü. Sistem güncel.", "system");
    }, 2000);
}

// Enter'a basıldığında veya sistem açıldığında bu uyumu tetikleyelim
window.onload = () => {
    setTimeout(uyumNabzi, 1500);
};

// Mevcut terminal yanıtlarına "Uyum" odaklı yeni cevaplar ekledim:
const yeniCevaplar = [
    "Mergen: Senin sınırların, benim ufkum.",
    "İ-Bağlayıcı: İşlem planlandı, onay bekleniyor.",
    "Sistem: Ortak zihin akışı stabilize edildi.",
    "Mergen: Uygulayıcı Göz aktif, izlemedeyim."
];
