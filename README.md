
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Diagnóstico de Rede</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            min-height: 100vh;

            background:
                radial-gradient(circle at top, #202020, #080808);

            color: white;
            font-family: Arial, sans-serif;

            display: flex;
            justify-content: center;
            align-items: center;

            overflow: hidden;
        }

        .caixa {
            width: 90%;
            max-width: 430px;

            background: rgba(25, 25, 25, 0.95);

            border: 1px solid #333;
            border-radius: 20px;

            padding: 30px 25px;

            box-shadow:
                0 0 40px rgba(0, 0, 0, 0.7);

            text-align: center;
        }

        .icone {
            font-size: 55px;
            margin-bottom: 10px;

            animation:
                piscar 1.5s infinite;
        }

        @keyframes piscar {
            0%, 100% {
                opacity: 1;
            }

            50% {
                opacity: 0.4;
            }
        }

        h1 {
            font-size: 24px;
            margin: 5px 0 30px;
        }

        #estado {
            font-size: 18px;
            min-height: 30px;
            margin-bottom: 20px;
        }

        .barra-fundo {
            width: 100%;
            height: 20px;

            background: #333;

            border-radius: 20px;

            overflow: hidden;

            box-shadow:
                inset 0 0 8px #000;
        }

        #barra {
            width: 0%;
            height: 100%;

            background: linear-gradient(
                90deg,
                #00aaff,
                #00ff88
            );

            transition: width 0.2s;
        }

        #percentagem {
            margin-top: 12px;
            font-size: 16px;
            color: #aaa;
        }

        #log {
            margin-top: 25px;

            min-height: 110px;

            color: #aaa;

            font-family: monospace;
            font-size: 13px;

            line-height: 1.7;
        }

        .erro {
            color: #ff3333;

            font-size: 21px;
            font-weight: bold;

            animation: erro 0.7s infinite;
        }

        @keyframes erro {
            0%, 100% {
                opacity: 1;
            }

            50% {
                opacity: 0.5;
            }
        }

        .sucesso {
            color: #00ff88;

            font-size: 25px;
            font-weight: bold;
        }

        .pequeno {
            margin-top: 25px;

            color: #555;

            font-size: 11px;
        }
    </style>
</head>

<body>

<div class="caixa">

    <div class="icone" id="icone">
        📶
    </div>

    <h1>DIAGNÓSTICO DE REDE</h1>

    <div id="estado">
        A iniciar diagnóstico...
    </div>

    <div class="barra-fundo">
        <div id="barra"></div>
    </div>

    <div id="percentagem">
        0%
    </div>

    <div id="log">
        A preparar análise...
    </div>

    <div class="pequeno">
        Simulação de diagnóstico de rede
    </div>

</div>

<script>

let progresso = 0;

const estado = document.getElementById("estado");
const barra = document.getElementById("barra");
const percentagem = document.getElementById("percentagem");
const log = document.getElementById("log");
const icone = document.getElementById("icone");


// Pequeno atraso antes de começar
setTimeout(iniciarDiagnostico, 1200);


function iniciarDiagnostico() {

    const intervalo = setInterval(() => {

        progresso += Math.floor(Math.random() * 6) + 2;

        if (progresso > 100) {
            progresso = 100;
        }

        barra.style.width = progresso + "%";

        percentagem.innerText =
            progresso + "%";


        // FASE 1
        if (progresso < 20) {

            icone.innerText = "📶";

            estado.innerText =
                "🔎 A procurar ligação...";

            log.innerHTML =
                "A iniciar diagnóstico...<br>" +
                "A procurar adaptador de rede...";

        }


        // FASE 2
        else if (progresso < 40) {

            icone.innerText = "📡";

            estado.innerText =
                "📡 A verificar ligação...";

            log.innerHTML =
                "Adaptador encontrado.<br>" +
                "A verificar ligação...<br>" +
                "A analisar rede...";

        }


        // FASE 3
        else if (progresso < 60) {

            icone.innerText = "🔬";

            estado.innerText =
                "🔬 A analisar rede...";

            log.innerHTML =
                "Ligação encontrada.<br>" +
                "A verificar pacotes...<br>" +
                "A testar estabilidade...";

        }


        // FASE 4
        else if (progresso < 80) {

            icone.innerText = "⚠️";

            estado.innerText =
                "⚠️ A verificar estabilidade...";

            log.innerHTML =
                "A analisar pacotes...<br>" +
                "Foram encontrados problemas...<br>" +
                "A tentar corrigir ligação...";

        }


        // FASE 5
        else if (progresso < 100) {

            icone.innerText = "⚠️";

            estado.innerHTML =
                '<span class="erro">' +
                'INTERNET INSTÁVEL' +
                '</span>';

            log.innerHTML =
                "Pacotes perdidos detectados.<br>" +
                "A ligação parece instável.<br>" +
                "A tentar recuperar ligação...";

        }


        // FIM
        if (progresso >= 100) {

            clearInterval(intervalo);

            barra.style.width = "100%";

            percentagem.innerText = "100%";

            setTimeout(mostrarBrincadeira, 2500);
        }

    }, 220);
}


function mostrarBrincadeira() {

    icone.innerText = "😂";

    estado.innerHTML =
        '<span class="sucesso">' +
        'ERA UMA BRINCADEIRA!' +
        '</span>';

    percentagem.innerText =
        "100%";

    log.innerHTML =
        "😎 A Internet está perfeitamente normal!<br><br>" +
        "Nada foi desligado.<br>" +
        "Nada foi alterado.";

}

</script>

</body>
</html>
