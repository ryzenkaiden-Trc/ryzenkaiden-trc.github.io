<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>GIXESH Obfuscate</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Unbounded:wght@500;700;900&family=Instrument+Sans:wght@400;500;600&display=swap">
<style>
:root{--bg:#030304;--ink:#EEF1F4;--mute:#9AA3AD;--line:#262A30;--card:#0A0B0D;--hi:#8FD3FF;--danger:#FF5A4A;--dot:200,208,216;--c1:#F6F8FA;--c2:#8E98A3;--c3:#4A5159;--c4:#DDE2E7;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:light){:root:not([data-theme="dark"]){--bg:#E8EBEF;--ink:#08090B;--mute:#4B545E;--line:#C3C9D0;--card:#F6F7F9;--hi:#0B63B8;--danger:#C62A1B;--dot:40,48,58;--c1:#0B0C0E;--c2:#59626C;--c3:#A9B1BA;--c4:#2A2F35}}
:root[data-theme="light"]{--bg:#E8EBEF;--ink:#08090B;--mute:#4B545E;--line:#C3C9D0;--card:#F6F7F9;--hi:#0B63B8;--danger:#C62A1B;--dot:40,48,58;--c1:#0B0C0E;--c2:#59626C;--c3:#A9B1BA;--c4:#2A2F35}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:1.05rem/1.6 "Instrument Sans",system-ui,sans-serif;overflow-x:hidden}
#bg{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;opacity:.5}
.wrap{position:relative;max-width:1040px;margin:0 auto;padding:0 20px}
:focus-visible{outline:2px solid var(--hi);outline-offset:3px}
h1,h2,.u{font-family:"Unbounded",system-ui,sans-serif}
.top{display:flex;justify-content:space-between;align-items:center;padding:20px 0}
.brand{font:700 .95rem "Unbounded",system-ui,sans-serif;letter-spacing:.04em}
.chip{display:flex;align-items:center;gap:10px;font-size:.9rem;color:var(--mute);border:1px solid var(--line);padding:6px 14px;border-radius:99px}
.chip i{width:8px;height:8px;border-radius:50%;background:#35D07F;animation:pulse 2s ease-out infinite}
@keyframes pulse{0%{box-shadow:0 0 0 0 rgba(53,208,127,.6)}100%{box-shadow:0 0 0 10px rgba(53,208,127,0)}}
.hero{padding:56px 0 36px}
h1{position:relative;margin:0;font-weight:900;line-height:.98;font-size:clamp(2.2rem,11vw,6.2rem);letter-spacing:-.03em;animation:reveal 1.6s cubic-bezier(.65,0,.2,1) .3s both}
@keyframes reveal{from{clip-path:inset(-10% 100% -10% 0)}to{clip-path:inset(-10% -2% -10% 0)}}
.chrome{display:block;background:linear-gradient(100deg,var(--c1) 0,var(--c3) 12%,var(--c4) 25%,var(--c2) 38%,var(--c1) 50%,var(--c3) 62%,var(--c4) 75%,var(--c2) 88%,var(--c1) 100%);background-size:200% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;animation:sheen 8s linear infinite}
@keyframes sheen{to{background-position:200% 0}}
.outline{display:block;color:transparent;-webkit-text-stroke:2px var(--ink)}
.beam{position:absolute;top:-6%;bottom:-6%;left:0;width:3px;background:var(--hi);box-shadow:0 0 28px 8px var(--hi);opacity:0;animation:beam 1.6s cubic-bezier(.65,0,.2,1) .3s both}
@keyframes beam{0%{left:0;opacity:1}92%{opacity:1}100%{left:100%;opacity:0}}
.late{opacity:0;animation:fade .8s ease-out 1.6s forwards}
@keyframes fade{to{opacity:1}}
.lede{max-width:36em;color:var(--mute);margin:24px 0 0}
.tool{display:grid;gap:16px;grid-template-columns:repeat(auto-fit,minmax(min(100%,420px),1fr))}
.panel{border:1px solid var(--line);border-radius:16px;background:var(--card);padding:18px;min-width:0}
.ph{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-bottom:12px;font:600 .8rem "Unbounded",system-ui,sans-serif;letter-spacing:.04em;text-transform:uppercase;color:var(--mute)}
textarea{display:block;width:100%;height:300px;resize:vertical;background:transparent;color:var(--ink);border:1px solid var(--line);border-radius:10px;padding:12px;font:13px/1.5 ui-monospace,Menlo,Consolas,monospace;transition:border-color .3s}
textarea:focus{border-color:var(--hi);outline:none}
.sm{font:600 .85rem "Instrument Sans",system-ui,sans-serif;color:var(--hi);background:none;border:1px solid var(--line);border-radius:99px;padding:5px 14px;cursor:pointer;text-transform:none;letter-spacing:0}
.sm:hover{border-color:var(--hi)}
.opts{display:flex;flex-wrap:wrap;gap:18px;align-items:center;margin:18px 0 0;color:var(--mute);font-size:.95rem}
.opts label{display:flex;align-items:center;gap:8px}
select{background:var(--card);color:var(--ink);border:1px solid var(--line);border-radius:8px;padding:6px 10px;font:inherit}
.go{position:relative;display:block;width:100%;margin-top:18px;padding:18px;border:0;border-radius:14px;cursor:pointer;font:800 1.05rem "Unbounded",system-ui,sans-serif;letter-spacing:.04em;color:var(--bg);background:linear-gradient(100deg,var(--c1),var(--c2),var(--c4),var(--c2),var(--c1));background-size:250% 100%;transition:background-position .8s,transform .2s}
.go:hover{background-position:100% 0;transform:translateY(-2px)}
.go:disabled{opacity:.7;cursor:progress}
.prog{height:4px;border-radius:4px;background:var(--line);margin-top:16px;overflow:hidden}
.prog i{display:block;height:100%;width:0;background:var(--hi);box-shadow:0 0 12px var(--hi);transition:width .45s ease-out}
.stage{min-height:1.6em;margin:8px 0 0;font:500 .85rem ui-monospace,Menlo,Consolas,monospace;color:var(--hi)}
.flash{animation:sweep 1.1s cubic-bezier(.6,0,.2,1)}
@keyframes sweep{from{clip-path:inset(0 100% 0 0)}to{clip-path:inset(0 0 0 0)}}
.shake{animation:shake .4s}
@keyframes shake{25%{transform:translateX(-6px)}75%{transform:translateX(6px)}}
.stats{display:flex;flex-wrap:wrap;gap:24px;margin-top:14px;color:var(--mute);font-size:.9rem}
.stats b{display:block;font:700 1.05rem "Unbounded",system-ui,sans-serif;color:var(--ink)}
.note{margin:28px 0 0;padding:16px 18px;border-left:3px solid var(--danger);color:var(--mute);font-size:.95rem;max-width:46em}
footer{margin:64px 0 0;padding:26px 0 56px;border-top:1px solid var(--line);color:var(--mute);font-size:.95rem}
@media (prefers-reduced-motion:reduce){h1,.chrome,.beam,.chip i{animation:none}.beam{display:none}.late{animation:none;opacity:1}.flash,.shake{animation:none}.prog i{transition:none}}
</style>
</head>
<body>
<canvas id="bg" aria-hidden="true"></canvas>
<main class="wrap">
<div class="top"><span class="brand">GIXESH</span><span class="chip"><i></i>Encoder online</span></div>
<header class="hero">
<h1><span class="chrome">GIXESH</span><span class="outline">OBFUSCATE</span><span class="beam"></span></h1>
<p class="lede late">Paste a Lua script and get it back as an encrypted byte array. The bytes are chained, shuffled and checksum-sealed — Level 5 also runs the decoder itself through a randomized-opcode VM. Every build is different.</p>
</header>

<div class="tool">
<div class="panel">
<div class="ph"><span>Your Lua script</span><span><button class="sm" id="sample">Sample</button> <button class="sm" id="clear">Clear</button></span></div>
<textarea id="src" spellcheck="false" placeholder="Paste your Lua code here"></textarea>
</div>
<div class="panel">
<div class="ph"><span>Obfuscated output</span><button class="sm" id="copy">Copy</button></div>
<textarea id="out" spellcheck="false" readonly placeholder="Your obfuscated script appears here"></textarea>
<div class="stats"><span><b id="s1">0</b>input bytes</span><span><b id="s2">0</b>output bytes</span><span><b id="s3">-</b>build seed</span><span><b id="s4">-</b>protection level</span></div>
</div>
</div>

<div class="opts">
<label>Protection <select id="lvl"><option value="1">Level 1 Basic</option><option value="2">Level 2 Strong</option><option value="3">Level 3 Heavy</option><option value="4">Level 4 Maximum</option><option value="5" selected>Level 5 VM Shield</option></select></label>
<label>Variable names <select id="style"><option value="hex">Hex (_0xA3F1)</option><option value="il">Confusing (lIlIlI)</option><option value="rnd">Random letters</option></select></label>
<label><input type="checkbox" id="one" checked> Single line</label>
<label><input type="checkbox" id="hdr" checked> Header comment</label>
</div>
<button class="go" id="go">OBFUSCATE</button>
<div class="prog"><i id="bar"></i></div>
<p class="stage" id="stage" aria-live="polite"></p>

<p class="note">Made By Scripterblabla</p>
<footer>GIXESH Obfuscate. Runs entirely in your browser, so your script is never uploaded.</footer>
</main>
<script>
(function(){
var $=function(i){return document.getElementById(i)},d=document.documentElement,rm=matchMedia("(prefers-reduced-motion: reduce)").matches;
function rnd(n){return Math.floor(Math.random()*n)}
function lcg(s){return(s*75+74)%65537}
function ne(x){var m=rnd(3);if(m===0)return String(x);if(m===1)return"0x"+x.toString(16);var r=1+rnd(900);return"("+(x+r)+"-"+r+")"}
function namer(st){var used={};return function(){var n,k,a="abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
do{if(st==="hex")n="_0x"+(4096+rnd(61000)).toString(16).toUpperCase();
else if(st==="il"){n="l";for(k=0;k<9+rnd(5);k++)n+=rnd(2)?"I":"l"}
else{n="";for(k=0;k<10;k++)n+=a[rnd(52)]}}while(used[n]);used[n]=1;return n}}
function cipherFwd(arr,seed){var k=seed,p=0,out=new Array(arr.length);for(var i=0;i<arr.length;i++){k=lcg(k);var e=(arr[i]+k%256+p)%256;out[i]=e;p=e}return out}
function shuffleFwd(arr,seed){var n=arr.length,a=arr.slice(),s=seed,i,j,t;for(i=n;i>=2;i--){s=lcg(s);j=s%i+1;t=a[i-1];a[i-1]=a[j-1];a[j-1]=t}return a}
function litArr(a,one){return"{"+a.map(function(b,x){var q=rnd(4)===0?"0x"+b.toString(16):String(b);return(!one&&x%24===23)?q+"\n":q}).join(",")+"}"}

function build(src,o){
var level=Math.max(1,Math.min(5,+o.level||1));
var bytes=Array.from(new TextEncoder().encode(src)),n=bytes.length,i;
if(!n)throw new Error("Paste a script first");
var chk=0;for(i=0;i<n;i++)chk=(chk+bytes[i]*(i%7+1))%65521;

var rounds=level,shufR=level,data=bytes,cipherSeeds=[],shuffleSeeds=[];
for(i=0;i<rounds;i++){var cs=1+rnd(65535);cipherSeeds.push(cs);data=cipherFwd(data,cs)}
for(i=0;i<shufR;i++){var ss=1+rnd(65535);shuffleSeeds.push(ss);data=shuffleFwd(data,ss)}

var chunkCount=level>=4?6:(level>=3?3:1);
var sz=Math.ceil(n/chunkCount),chunks=[];
for(i=0;i<chunkCount;i++)chunks.push(data.slice(i*sz,(i+1)*sz));
var perm=chunks.map(function(_,ix){return ix});
for(i=perm.length-1;i>0;i--){var jx=rnd(i+1),tmp=perm[i];perm[i]=perm[jx];perm[jx]=tmp}
var invperm=new Array(perm.length);perm.forEach(function(trueIdx,slot){invperm[trueIdx]=slot});
var order=invperm.map(function(x){return x+1});

var N=namer(o.style),m={};
"CH ORDER CS SS CHK UNCI UNSH D Nn T O SRC F Em POS BLK X I J K P E V S PROGv PC OPV OPND".split(" ").forEach(function(k){m[k]=N()});
var gateCount=level>=4?2:(level>=3?1:0),gates=[];for(i=0;i<gateCount;i++)gates.push(N());
var decoyCount=level>=4?2:(level>=3?1:0),decoys=[];for(i=0;i<decoyCount;i++)decoys.push(N());

var L=[];
var chTables=perm.map(function(trueIdx){return litArr(chunks[trueIdx],o.one)});
if(decoys.length){var pos=Math.floor(chTables.length/2);decoys.forEach(function(dn,di){
var fake=[];for(var q=0;q<Math.max(8,sz);q++)fake.push(rnd(256));
L.push("local "+dn+"="+litArr(fake,o.one))})}
L.push("local "+m.CH+"={"+chTables.join(",")+"}");
L.push("local "+m.ORDER+"={"+order.map(ne).join(",")+"}");
L.push("local "+m.CS+"={"+cipherSeeds.map(ne).join(",")+"}");
L.push("local "+m.SS+"={"+shuffleSeeds.map(ne).join(",")+"}");
L.push("local "+m.CHK+"="+ne(chk));
L.push("local function "+m.UNCI+"("+m.D+","+m.S+","+m.Nn+")local "+m.K+","+m.P+"="+m.S+",0;"+
"for "+m.I+"=1,"+m.Nn+" do "+m.K+"=("+m.K+"*"+ne(75)+"+"+ne(74)+")%"+ne(65537)+";local "+m.E+"="+m.D+"["+m.I+"];"+
m.D+"["+m.I+"]=("+m.E+"-"+m.K+"%"+ne(256)+"-"+m.P+")%"+ne(256)+";"+m.P+"="+m.E+" end end");
L.push("local function "+m.UNSH+"("+m.D+","+m.S+","+m.Nn+")local "+m.J+"={};local "+m.K+"="+m.S+";"+
"for "+m.I+"="+m.Nn+","+ne(2)+",-1 do "+m.K+"=("+m.K+"*"+ne(75)+"+"+ne(74)+")%"+ne(65537)+";"+m.J+"["+m.I+"]="+m.K+"%"+m.I+"+1 end;"+
"for "+m.I+"="+ne(2)+","+m.Nn+" do local "+m.X+"="+m.J+"["+m.I+"];"+m.D+"["+m.I+"],"+m.D+"["+m.X+"]="+m.D+"["+m.X+"],"+m.D+"["+m.I+"] end end");

var inner;
if(level===5){
var semOps=["RECON","UNSH","UNCI","VERIFY","TOSTR","RUN"],junkCount=5;
var pool=[];for(i=0;i<256;i++)pool.push(i);
for(i=pool.length-1;i>0;i--){var jx=rnd(i+1),tp=pool[i];pool[i]=pool[jx];pool[jx]=tp}
var byteOf={};semOps.forEach(function(op,idx){byteOf[op]=pool[idx]});
var junkBytes=pool.slice(semOps.length,semOps.length+junkCount);
var junkHasOperand=junkBytes.map(function(){return rnd(2)===0});

var seq=[{op:"RECON"}];
for(i=rounds;i>=1;i--)seq.push({op:"UNSH",operand:i});
for(i=rounds;i>=1;i--)seq.push({op:"UNCI",operand:i});
seq.push({op:"VERIFY"});seq.push({op:"TOSTR"});seq.push({op:"RUN"});
for(i=0;i<junkCount;i++){var at=1+rnd(seq.length);seq.splice(at,0,{op:"JUNK",byte:junkBytes[i],hasOperand:junkHasOperand[i]})}

var words=[];
seq.forEach(function(ins){
if(ins.op==="JUNK"){words.push(ins.byte);if(ins.hasOperand)words.push(rnd(256))}
else{words.push(byteOf[ins.op]);if(ins.op==="UNSH"||ins.op==="UNCI")words.push(ins.operand)}
});
L.push("local "+m.PROGv+"={"+words.map(ne).join(",")+"}");

var h={};
h.RECON=m.D+"={};"+m.Nn+"=0;for "+m.POS+"=1,#"+m.ORDER+" do local "+m.BLK+"="+m.CH+"["+m.ORDER+"["+m.POS+"]];for "+m.X+"=1,#"+m.BLK+" do "+m.Nn+"="+m.Nn+"+1;"+m.D+"["+m.Nn+"]="+m.BLK+"["+m.X+"] end end;"+m.PC+"="+m.PC+"+1";
h.UNSH="local "+m.OPND+"="+m.PROGv+"["+m.PC+"+1];"+m.UNSH+"("+m.D+","+m.SS+"["+m.OPND+"],"+m.Nn+");"+m.PC+"="+m.PC+"+2";
h.UNCI="local "+m.OPND+"="+m.PROGv+"["+m.PC+"+1];"+m.UNCI+"("+m.D+","+m.CS+"["+m.OPND+"],"+m.Nn+");"+m.PC+"="+m.PC+"+2";
h.VERIFY="local "+m.T+"=0;for "+m.I+"=1,"+m.Nn+" do "+m.T+"=("+m.T+"+"+m.D+"["+m.I+"]*(("+m.I+"-1)%"+ne(7)+"+1))%"+ne(65521)+" end;if "+m.T+"~="+m.CHK+" then error(\"GIXESH: script was modified\") end;"+m.PC+"="+m.PC+"+1";
h.TOSTR="local "+m.O+"={};for "+m.I+"=1,"+m.Nn+" do "+m.O+"["+m.I+"]=string.char("+m.D+"["+m.I+"]) end;"+m.SRC+"=table.concat("+m.O+");"+m.PC+"="+m.PC+"+1";
h.RUN=m.PC+"="+m.PC+"+1;local "+m.F+","+m.Em+"=(loadstring or load)("+m.SRC+");if not "+m.F+" then error("+m.Em+") end;local "+m.OPND+"2=("+m.CHK+"%2);if "+m.OPND+"2==("+m.CHK+"%2) then return "+m.F+"(...) else error(\"GIXESH: integrity\") end";

var branches=semOps.map(function(op){return{byte:byteOf[op],code:h[op]}});
junkBytes.forEach(function(jb,idx){branches.push({byte:jb,code:m.PC+"="+m.PC+"+"+(junkHasOperand[idx]?"2":"1")})});
for(i=branches.length-1;i>0;i--){var jx2=rnd(i+1),tp2=branches[i];branches[i]=branches[jx2];branches[jx2]=tp2}
var ifs=branches.map(function(b,idx){return(idx===0?"if ":"elseif ")+m.OPV+"=="+b.byte+" then "+b.code}).join(o.one?" ":"\n");

inner=["local "+m.D+","+m.Nn+","+m.SRC+"={},0,\"\"","local "+m.PC+"=1","while "+m.PC+"<=#"+m.PROGv+" do",
"local "+m.OPV+"="+m.PROGv+"["+m.PC+"]",ifs,"else "+m.PC+"="+m.PC+"+1 end","end"].join(o.one?" ":"\n");
}else{
var body=[];
body.push("local "+m.D+",_w={},0");
body.push("for "+m.POS+"=1,#"+m.ORDER+" do local "+m.BLK+"="+m.CH+"["+m.ORDER+"["+m.POS+"]];"+
"for "+m.X+"=1,#"+m.BLK+" do _w=_w+1;"+m.D+"[_w]="+m.BLK+"["+m.X+"] end end");
body.push("local "+m.Nn+"=_w");
body.push("for "+m.I+"=#"+m.SS+",1,-1 do "+m.UNSH+"("+m.D+","+m.SS+"["+m.I+"],"+m.Nn+") end");
body.push("for "+m.I+"=#"+m.CS+",1,-1 do "+m.UNCI+"("+m.D+","+m.CS+"["+m.I+"],"+m.Nn+") end");
body.push("local "+m.T+"=0;local "+m.O+"={};for "+m.I+"=1,"+m.Nn+" do "+m.O+"["+m.I+"]=string.char("+m.D+"["+m.I+"]);"+
m.T+"=("+m.T+"+"+m.D+"["+m.I+"]*(("+m.I+"-1)%"+ne(7)+"+1))%"+ne(65521)+" end");
body.push("if "+m.T+"~="+m.CHK+" then error(\"GIXESH: script was modified\") end");
body.push("local "+m.SRC+"=table.concat("+m.O+")");
if(level>=2)body.push("if #"+m.SRC+"~="+ne(n)+" then error(\"GIXESH: length mismatch\") end");
body.push("local "+m.F+","+m.Em+"=(loadstring or load)("+m.SRC+")");
body.push("if not "+m.F+" then error("+m.Em+") end");
if(level>=2){
body.push("local "+m.T+"2=("+m.CHK+"%2)");
body.push("if "+m.T+"2==("+m.CHK+"%2) then return "+m.F+"(...) else error(\"GIXESH: integrity\") end")
}else body.push("return "+m.F+"(...)");
inner=body.join(o.one?" ":"\n");
}
if(gates.length){
L.push("local "+gates[0]+"=function(...)"+(o.one?" ":"\n")+inner+(o.one?" ":"\n")+"end");
for(i=1;i<gates.length;i++)L.push("local "+gates[i]+"=function(...) return "+gates[i-1]+"(...) end");
L.push("return "+gates[gates.length-1]+"(...)");
}else{
L.push(inner);
}

var out=L.join(o.one?" ":"\n");
if(o.hdr)out="--[[ Obfuscated with GIXESH Obfuscate - Level "+level+" ]]"+(o.one?" ":"\n")+out;
return{code:out,seed:cipherSeeds.concat(shuffleSeeds).map(function(x){return x.toString(16).toUpperCase()}).join("").slice(0,10),n:n,level:level,rounds:rounds,chunks:chunkCount}}

var src=$("src"),out=$("out"),go=$("go"),bar=$("bar"),stage=$("stage");
$("sample").onclick=function(){src.value='local Players = game:GetService("Players")\nlocal player = Players.LocalPlayer\nprint("Hello from GIXESH, " .. player.Name)'};
$("clear").onclick=function(){src.value="";out.value="";$("s1").textContent="0";$("s2").textContent="0";$("s3").textContent="-"};
$("copy").onclick=function(){if(!out.value)return;var b=$("copy");function ok(){b.textContent="Copied";setTimeout(function(){b.textContent="Copy"},1400)}
function fb(){out.select();try{document.execCommand("copy");ok()}catch(x){}}
if(navigator.clipboard)navigator.clipboard.writeText(out.value).then(ok,fb);else fb()};
function wait(ms){return new Promise(function(r){setTimeout(r,rm?0:ms)})}
go.onclick=async function(){
if(!src.value.trim()){src.classList.remove("shake");void src.offsetWidth;src.classList.add("shake");src.focus();return}
var lvl=+$("lvl").value,res;
try{res=build(src.value,{style:$("style").value,one:$("one").checked,hdr:$("hdr").checked,level:lvl})}catch(x){stage.textContent="Something went wrong: "+x.message;return}
var stages=["Encrypting bytes ("+res.rounds+" round"+(res.rounds>1?"s":"")+")","Shuffling the order ("+res.rounds+" pass"+(res.rounds>1?"es":"")+")",
res.chunks>1?"Splitting into "+res.chunks+" chunks and reordering":"Sealing the checksum",
lvl===5?"Compiling to randomized VM bytecode":"Packing level "+lvl+" byte array"];
go.disabled=true;boost=4+lvl;out.value="";
for(var i=0;i<stages.length;i++){stage.textContent="> "+stages[i]+"...";bar.style.width=((i+1)*25-8)+"%";await wait(350+lvl*60)}
bar.style.width="100%";out.value=res.code;out.classList.remove("flash");void out.offsetWidth;out.classList.add("flash");
$("s1").textContent=res.n.toLocaleString();$("s2").textContent=res.code.length.toLocaleString();$("s3").textContent=res.seed;$("s4").textContent="L"+res.level+" / "+res.rounds+"x";
stage.textContent="> Done. Copy your script.";boost=1;go.disabled=false;
setTimeout(function(){bar.style.width="0"},900)};

var cv=$("bg"),cx=cv.getContext("2d"),W,H,cols,dr,rgb,boost=1;
function size(){W=cv.width=innerWidth;H=cv.height=innerHeight;cols=Math.ceil(W/24);dr=[];for(var c=0;c<cols;c++)dr.push(Math.random()*H/16);rgb=getComputedStyle(d).getPropertyValue("--dot").trim();if(rm)frame(true)}
function frame(once){cx.clearRect(0,0,W,H);cx.font="14px ui-monospace,Menlo,monospace";
for(var c=0;c<cols;c++){for(var r=0;r<9;r++){var y=(dr[c]-r)*16;if(y<-16||y>H+16)continue;
var b=((c*37+Math.floor(dr[c])-r)*73)&255;cx.fillStyle="rgba("+rgb+","+(.55-r*.06)+")";cx.fillText(("0"+b.toString(16)).slice(-2),c*24,y)}
if(!once){dr[c]+=.1*boost*(1+c%3*.35);if(dr[c]*16>H+150)dr[c]=-rnd(25)}}
if(once!==true)requestAnimationFrame(frame)}
size();addEventListener("resize",size);matchMedia("(prefers-color-scheme: light)").addEventListener("change",size);
if(!rm)requestAnimationFrame(frame);
})();
</script>
</body>
</html>

