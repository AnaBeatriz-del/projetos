Jogo da velha em HTML

Este é um projeto simples de um jogo feito com HTML/CSS e JavaScript. Ele roda direto no navegador e pode ser usado para praticar lógica, estrutura de páginas e desenvolvimento web básico.


<!DOCTYPE html>
<html lang="pt-BR" >
<head>
    <meta charset="UTF-8">
    <title>Jogo - Pedra, Papel ou Tesoura</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 30px;
            background-color: #f2f2f2;
        }
        #game {
            display: none;
        }
        button {
            padding: 10px 20px;
            margin: 10px;
            font-size: 18px;
            cursor: pointer;
        }
        #resultado {
            margin-top: 20px;
            font-weight: bold;
        }
        #placar {
            margin-top: 30px;
            font-size: 20px;
            background-color: #fff;
            padding: 15px;
            border-radius: 10px;
            display: inline-block;
        }
    </style>
</head>
<body>
    <h1>Jogo: Pedra, Papel ou Tesoura</h1>
    <div id="inicio">
        <label>Digite sua idade: </label>
        <input type="number" id="idadeInput" />
        <button onclick="verificarIdade()">Começar o jogo</button>
    </div>
    <div id="game">
        <h2>Escolha sua jogada:</h2>
        <button onclick="jogar(1)">Pedra 🪨</button>
        <button onclick="jogar(2)">Papel 📄</button>
        <button onclick="jogar(3)">Tesoura ✂️</button>
        <p id="resultado"></p>
    <div id="placar">
        👤Jogador: <span id="VitoriasJogador">0</span><br>
        💻Computador: <span id="VitoriasComputador">0</span>
    </div>
    <br><br>
    <button onclick="reiniciarJogo()">Jogar Novamente</button>
    </div>
    <script>
        let VitoriasJogador = 0;
        let VitoriasComputador = 0;
        function verificarIdade() {
            const idade = parseInt(document.getElementById('idadeInput').value);
            if (idade >=18) {
                document.getElementById('inicio').style.display = 'none';
                document.getElementById('game').style.display = 'block';
            } else {
                alert("você NÃO pode jogar.");
            }
        }
        function jogar(escolhaJogador) {
            const escolhas = ["", "Pedra", "Papel", "Tesoura"];
            const escolhaComputador = Math.floor(Math.random()* 3) + 1;
            let resultado = `Você escolheu ${escolhas[escolhaJogador]}<br>`;
            resultado += `Computador escolheu ${escolhas[escolhaComputador]}<br>`;
            if (escolhaJogador === escolhaComputador){
                resultado +=  "Resultado: Empate!"
            } else if (
                (escolhaJogador === 1 && escolhaComputador === 3) ||
                (escolhaJogador === 2 && escolhaComputador === 1) ||
                (escolhaJogador === 3 && escolhaComputador === 2)
            ) {
                resultado += "Resultado: Você venceu! 🎉";
                VitoriasJogador++;
            } else {
                resultado += "Resultado: Computador venceu!";
                VitoriasComputador++;
            }
            document.getElementById('resultado').innerHTML = resultado;
            atualizarPlacar();
        }
        function atualizarPlacar() {
            document.getElementById('VitoriasJogador').textContent = VitoriasJogador;
            document.getElementById('VitoriasComputador').textContent = VitoriasComputador;
        }
        function reiniciarJogo(){
        document.getElementById('resultado').innerHTML  = "";
        }
    </script>

</body>
</html>
