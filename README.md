<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Simulado Técnico em TI - Redes</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body{
  font-family: Arial, sans-serif;
  background:#f2f2f2;
  margin:0;
  padding:10px;
}
h1,h2{
  text-align:center;
}
.question{
  background:#fff;
  padding:15px;
  margin-bottom:12px;
  border-radius:8px;
}
.question h3{
  font-size:16px;
}
label{
  display:block;
  margin:6px 0;
}
button{
  width:100%;
  padding:15px;
  font-size:18px;
  background:#1a73e8;
  color:#fff;
  border:none;
  border-radius:8px;
}
.result{
  margin-top:15px;
  background:#e8f0fe;
  padding:15px;
  border-radius:8px;
  font-size:18px;
}
</style>
</head>
<body>

<h1>Simulado – Técnico em Tecnologia da Informação</h1>
<h2>Nível Médio/Técnico – Redes</h2>

<form id="quiz">

<script>
const perguntas = [
/* PORTUGUÊS 1–10 */
["O texto informativo tem como principal objetivo:",["Convencer o leitor","Emocionar","Informar de forma objetiva","Narrar fatos fictícios","Criticar opiniões"]],
["A concordância está correta em:",["Houveram problemas","Fazem dois anos","Existe muitas vagas","Há muitos candidatos","Devem ter ocorrido erro"]],
["A palavra 'infraestrutura' é formada por:",["Derivação sufixal","Derivação prefixal","Composição","Aglutinação","Abreviação"]],
["O sujeito da frase 'Ocorreram falhas no sistema' é:",["Oculto","Simples","Composto","Indeterminado","Inexistente"]],
["Sinônimo de 'essencial' é:",["Opcional","Dispensável","Fundamental","Irrelevante","Secundário"]],
["A crase é obrigatória em:",["Vou a escola","Cheguei a tarde","Entreguei à diretora","Fui a pé","Voltei a casa"]],
["O verbo está no plural corretamente em:",["Fazem calor","Existem dados","Há pessoas","Choveu problemas","Teve erros"]],
["A linguagem usada em editais é:",["Coloquial","Regional","Técnica e formal","Figurada","Literária"]],
["Antônimo de 'ineficiente' é:",["Lento","Falho","Eficaz","Inútil","Fraco"]],
["O plural correto de 'cidadão' é:",["Cidadãos","Cidadões","Cidadães","Cidadons","Cidadõeses"]],

/* INFORMÁTICA 11–20 */
["Qual é um sistema operacional?",["Excel","Windows","Chrome","BIOS","Google"]],
["Atalho para copiar no Windows:",["Ctrl+X","Ctrl+V","Ctrl+C","Ctrl+Z","Ctrl+A"]],
["Memória volátil é:",["HD","SSD","RAM","DVD","Pendrive"]],
["Software antivírus tem função de:",["Editar texto","Proteger contra malware","Criar planilhas","Compactar arquivos","Instalar drivers"]],
["Qual não é periférico?",["Mouse","Teclado","Monitor","Processador","Impressora"]],
["Extensão de arquivo do Word:",[".xls",".ppt",".docx",".pdf",".exe"]],
["Navegador de internet:",["Linux","Windows","Chrome","Android","BIOS"]],
["Backup serve para:",["Excluir arquivos","Proteger dados","Formatar PC","Instalar SO","Criar vírus"]],
["Planilha eletrônica:",["Word","Paint","Excel","Bloco de notas","PowerPoint"]],
["Ctrl+Alt+Del serve para:",["Desligar PC","Abrir navegador","Gerenciar tarefas","Copiar texto","Salvar arquivo"]],

/* LEGISLAÇÃO 21–30 */
["A Constituição garante acesso à educação:",["Opcional","Privado","Universal","Restrito","Pago"]],
["Servidor público deve agir com:",["Imparcialidade","Interesse próprio","Vantagem pessoal","Favorecimento","Negligência"]],
["Lei que trata da LGPD:",["8.112","9.394","13.709","11.091","10.520"]],
["Dado sensível inclui:",["Nome","CPF","Endereço","Dados de saúde","Telefone"]],
["Código de Ética exige:",["Desídia","Probidade","Omissão","Benefício próprio","Nepotismo"]],
["Educação básica vai dos:",["0 aos 14","4 aos 17","6 aos 18","7 aos 16","5 aos 15"]],
["Improbidade administrativa é:",["Ato legal","Erro técnico","Conduta dolosa","Opinião pessoal","Falta leve"]],
["Servidor deve prestar contas:",["Quando quiser","Nunca","Sempre","Apenas se solicitado","Somente judicialmente"]],
["Lei 8.112 trata de:",["CLT","Servidor público","Educação","Licitações","Saúde"]],
["Princípio da administração pública:",["Lucro","Moralidade","Competição","Exclusividade","Publicidade paga"]],

/* CONHECIMENTOS ESPECÍFICOS 31–50 */
["Modelo OSI possui quantas camadas?",["5","6","7","4","8"]],
["Protocolo de IP automático:",["DNS","FTP","DHCP","HTTP","SMTP"]],
["Equipamento que interliga redes:",["Switch","Hub","Roteador","Bridge","Repetidor"]],
["Camada do OSI responsável pelo IP:",["Sessão","Aplicação","Rede","Enlace","Física"]],
["Comando para testar conectividade:",["ipconfig","ping","nslookup","net use","netstat"]],
["DNS converte:",["IP em MAC","Nome em IP","MAC em IP","Texto em dados","Rede em host"]],
["Firewall serve para:",["Armazenar dados","Filtrar tráfego","Criar usuários","Editar arquivos","Formatar disco"]],
["Adware é:",["Vírus destrutivo","Malware de anúncios","Spyware","Ransomware","Trojan"]],
["Topologia em anel é:",["Linear","Circular","Estrela","Malha","Barramento"]],
["Protocolo seguro de arquivos:",["FTP","HTTP","SMTP","SFTP","POP3"]],
["Máscara 255.255.255.0 equivale a:",["/16","/8","/24","/30","/32"]],
["Switch atua na camada:",["Física","Rede","Aplicação","Enlace","Sessão"]],
["IPv4 possui quantos bits?",["32","64","128","16","8"]],
["Ping utiliza protocolo:",["TCP","UDP","ICMP","HTTP","FTP"]],
["Servidor DNS é responsável por:",["Armazenar arquivos","Distribuir IP","Resolver nomes","Filtrar pacotes","Criar rotas"]],
["Rede local é chamada:",["WAN","MAN","LAN","PAN","SAN"]],
["Protocolo de e-mail:",["HTTP","FTP","SMTP","SNMP","DHCP"]],
["Gateway padrão é:",["IP do host","IP do roteador","DNS","Firewall","Servidor"]],
["Nslookup consulta:",["IP","Gateway","DNS","Firewall","MAC"]],
["IA generativa serve para:",["Bloquear rede","Criar conteúdo","Formatar disco","Analisar logs","Criar usuários"]]
];

const gabarito = [
"C","D","B","B","C","C","B","C","C","A",
"B","C","C","B","D","C","C","B","C","C",
"C","A","C","D","B","B","C","C","B","B",
"C","C","C","C","B","B","B","B","B","D",
"C","D","A","C","C","B","C","C","C","B"
];

let html="";
for(let i=0;i<perguntas.length;i++){
 html+=`<div class="question">
 <h3>${i+1}. ${perguntas[i][0]}</h3>`;
 for(let j=0;j<5;j++){
   html+=`<label><input type="radio" name="q${i}" value="${String.fromCharCode(65+j)}"> ${perguntas[i][1][j]}</label>`;
 }
 html+="</div>";
}
document.write(html);
</script>

</form>

<button onclick="corrigir()">Finalizar Simulado</button>

<div id="resultado" class="result"></div>

<script>
function corrigir(){
 let acertos=0;
 for(let i=0;i<gabarito.length;i++){
   let marcada=document.querySelector(`input[name="q${i}"]:checked`);
   if(marcada && marcada.value===gabarito[i]) acertos++;
 }
 let erros=50-acertos;
 let status="";
 if(acertos<30) status="❌ NÃO CLASSIFICADA";
 else if(acertos<40) status="⚠️ CLASSIFICAÇÃO BAIXA";
 else status="✅ APROVADA / BOA CLASSIFICAÇÃO";
 document.getElementById("resultado").innerHTML=
 `Acertos: ${acertos}<br>Erros: ${erros}<br><strong>${status}</strong>`;
}
</script>

</body>
</html>
