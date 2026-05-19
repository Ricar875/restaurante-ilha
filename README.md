<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Restaurante da Ilha</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.10.0/tabler-icons.min.css">
<style>
  *{box-sizing:border-box;margin:0;padding:0}
  body{font-family:'Segoe UI',system-ui,sans-serif;background:#f0f4f2;min-height:100vh;display:flex;align-items:flex-start;justify-content:center;padding:16px}
  .app{width:100%;max-width:420px;background:#fff;border-radius:18px;overflow:hidden;box-shadow:0 4px 24px rgba(0,0,0,.10)}
  .hdr{background:#0F6E56;padding:20px 20px 14px;color:white}
  .hdr-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:3px}
  .logo{font-size:18px;font-weight:600;letter-spacing:-.2px}
  .logo small{font-size:11px;display:block;opacity:.75;font-weight:400;margin-top:1px}
  .badge-ok{background:#9FE1CB;color:#085041;font-size:11px;padding:3px 11px;border-radius:20px;font-weight:600}
  .hdr-data{font-size:11px;color:rgba(255,255,255,.65);margin-top:2px}
  .nav{display:flex;border-bottom:1px solid #e8ede9;background:#fff}
  .nb{flex:1;padding:10px 4px;font-size:11px;font-weight:500;border:none;background:none;cursor:pointer;color:#888;border-bottom:2px solid transparent;transition:all .15s}
  .nb.on{color:#0F6E56;border-bottom-color:#0F6E56}
  .nb i{display:block;font-size:18px;margin:0 auto 2px}
  .sec{display:none}.sec.on{display:block}
  .pad{padding:14px 16px}
  .lbl{font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:#999;margin:14px 0 8px}
  .lbl:first-child{margin-top:0}

  /* Cardápio */
  .dia-row{display:flex;align-items:center;gap:8px;margin-bottom:12px}
  .dia-pill{background:#E1F5EE;color:#085041;font-size:12px;font-weight:600;padding:3px 13px;border-radius:20px}
  .pc{background:#f7faf8;border-radius:10px;padding:11px 13px;margin-bottom:8px;display:flex;justify-content:space-between;align-items:flex-start}
  .pc.dest{background:#FFF4F0;border-left:3px solid #D85A30;border-radius:0 10px 10px 0}
  .pt{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:#999;margin-bottom:2px}
  .pn{font-size:13px;font-weight:600;color:#1a1a1a}
  .pd{font-size:11px;color:#888;margin-top:2px}
  .pp{font-size:14px;font-weight:600;color:#1D9E75;white-space:nowrap;margin-left:10px}
  .pc.dest .pp{color:#993C1D}

  /* Mesa */
  .mesa-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:12px}
  .mb{border:1px solid #e0e8e4;border-radius:10px;padding:13px 6px;text-align:center;cursor:pointer;background:#fff;transition:all .15s}
  .mb.livre{background:#E8F8F2;border-color:#5DCAA5}
  .mb.ocup{background:#FFF0EC;border-color:#F0997B}
  .mb.sel{border:2px solid #0F6E56;background:#E1F5EE}
  .mn{font-size:15px;font-weight:600;color:#1a1a1a}
  .ms{font-size:10px;margin-top:2px}
  .mb.livre .ms{color:#0F6E56}.mb.ocup .ms{color:#993C1D}
  .cb{background:#f7faf8;border-radius:10px;padding:12px}
  .cb-titulo{font-size:13px;font-weight:600;color:#1a1a1a;margin-bottom:8px}
  .ab{border:1px solid #e0e8e4;border-radius:8px;padding:9px 12px;background:#fff;cursor:pointer;display:flex;align-items:center;gap:8px;font-size:13px;color:#1a1a1a;width:100%;margin-bottom:6px;transition:background .12s}
  .ab:last-child{margin-bottom:0}
  .ab:hover{background:#E1F5EE}
  .ab i{color:#0F6E56;font-size:17px}

  /* WhatsApp */
  .wpp-hero{background:#E1F5EE;border-radius:12px;padding:14px;margin-bottom:12px;display:flex;align-items:center;gap:12px}
  .wpp-av{width:46px;height:46px;background:#0F6E56;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0}
  .wpp-av i{font-size:23px;color:white}
  .wpp-t{font-size:14px;font-weight:600;color:#085041}
  .wpp-s{font-size:12px;color:#0F6E56;margin-top:2px}
  .gbtn{display:block;width:100%;background:#25D366;color:white;border:none;border-radius:10px;padding:13px;font-size:14px;font-weight:600;cursor:pointer;margin-bottom:12px;text-decoration:none;text-align:center}
  .gbtn:hover{background:#1ebe5d}
  .wi{border:1px solid #e0e8e4;border-radius:10px;padding:11px 13px;margin-bottom:7px;background:#fff;display:flex;justify-content:space-between;align-items:center;cursor:pointer;text-decoration:none}
  .wi:hover{background:#f7faf8}
  .wi-l{font-size:13px;font-weight:600;color:#1a1a1a}
  .wi-s{font-size:11px;color:#888;margin-top:2px}
  .wi i{font-size:15px;color:#aaa}

  /* Fidelidade */
  .cartao{background:#0F6E56;border-radius:14px;padding:16px 18px;margin-bottom:14px;color:white}
  .ctop{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:12px}
  .cnome{font-size:14px;font-weight:600}
  .csub{font-size:11px;opacity:.75;margin-top:1px}
  .cnivel{background:#9FE1CB;color:#085041;font-size:10px;font-weight:600;padding:3px 10px;border-radius:20px}
  .cpts{font-size:30px;font-weight:700}
  .clab{font-size:12px;opacity:.8;margin-left:6px}
  .bwrap{background:rgba(255,255,255,.2);border-radius:20px;height:7px;overflow:hidden;margin:10px 0 4px}
  .bfill{background:#9FE1CB;height:7px;border-radius:20px;transition:width .5s}
  .binfo{display:flex;justify-content:space-between;font-size:10px;opacity:.8}
  .selos{display:grid;grid-template-columns:repeat(5,1fr);gap:7px;margin-bottom:12px}
  .selo{aspect-ratio:1;border-radius:8px;display:flex;align-items:center;justify-content:center;border:1.5px solid #ddd}
  .selo.ok{background:#E1F5EE;border-color:#1D9E75}
  .selo.ok i{color:#0F6E56;font-size:18px}
  .selo.prm{background:#FFF3DA;border:2px solid #EF9F27}
  .selo.prm i{color:#854F0B;font-size:18px}
  .selo.vz i{color:#ccc;font-size:18px}
  .rcard{background:#FFF3DA;border-radius:10px;padding:12px;margin-bottom:12px;display:flex;align-items:center;gap:10px}
  .ricon{width:38px;height:38px;background:#EF9F27;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0}
  .ricon i{font-size:19px;color:#412402}
  .rt{font-size:13px;font-weight:600;color:#412402}
  .rs{font-size:11px;color:#854F0B;margin-top:2px}
  .btnv{width:100%;background:#0F6E56;color:white;border:none;border-radius:10px;padding:13px;font-size:13px;font-weight:600;cursor:pointer;margin-bottom:8px}
  .btnv:hover{background:#085041}
  .btnr{width:100%;background:#EF9F27;color:#412402;border:none;border-radius:10px;padding:13px;font-size:13px;font-weight:600;cursor:pointer}
  .btnr:hover{background:#BA7517;color:white}
  .btnr:disabled{opacity:.4;cursor:not-allowed}
  .hist-item{display:flex;justify-content:space-between;align-items:center;padding:9px 0;border-bottom:1px solid #f0f0f0}
  .hist-item:last-child{border-bottom:none}
  .hav{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0}
  .hav.g{background:#E1F5EE}.hav.g i{color:#0F6E56;font-size:14px}
  .hav.r{background:#FFF3DA}.hav.r i{color:#854F0B;font-size:14px}
  .hd{font-size:12px;font-weight:600;color:#1a1a1a}
  .hda{font-size:10px;color:#999;margin-top:1px}
  .hpt{font-size:13px;font-weight:600}.hpt.pos{color:#0F6E56}.hpt.neg{color:#993C1D}

  .toast-bar{background:#0F6E56;color:white;padding:8px 16px;border-radius:20px;font-size:12px;text-align:center;margin-bottom:10px;display:none}
  .toast-bar.on{display:block}
  .rodape{padding:10px 16px;text-align:center;font-size:11px;color:#aaa;border-top:1px solid #f0f0f0}

  /* toast global flutuante */
  #gtoast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:#0F6E56;color:white;padding:9px 20px;border-radius:20px;font-size:13px;white-space:nowrap;display:none;z-index:999;box-shadow:0 4px 16px rgba(0,0,0,.2)}
</style>
</head>
<body>

<div id="gtoast"></div>

<div class="app">
  <div class="hdr">
    <div class="hdr-top">
      <div class="logo">🏝 Restaurante da Ilha<small>Paulo Afonso, BA</small></div>
      <div class="badge-ok">Aberto</div>
    </div>
    <div class="hdr-data" id="hdr-data"></div>
  </div>

  <nav class="nav">
    <button class="nb on" onclick="aba('cardapio',this)"><i class="ti ti-clipboard-list"></i>Cardápio</button>
    <button class="nb" onclick="aba('mesa',this)"><i class="ti ti-armchair"></i>Mesa</button>
    <button class="nb" onclick="aba('wpp',this)"><i class="ti ti-brand-whatsapp"></i>WhatsApp</button>
    <button class="nb" onclick="aba('fid',this)"><i class="ti ti-gift"></i>Fidelidade</button>
  </nav>

  <!-- CARDÁPIO -->
  <div id="cardapio" class="sec on">
    <div class="pad">
      <div class="dia-row">
        <span class="dia-pill" id="dia-pill"></span>
        <span style="font-size:12px;color:#888">Cardápio de hoje</span>
      </div>
      <div class="pc dest">
        <div><div class="pt">⭐ Prato do dia</div><div class="pn" id="prato-dia">—</div><div class="pd">Arroz, feijão, farofa, salada</div></div>
        <div class="pp">R$22</div>
      </div>
      <div class="pc">
        <div><div class="pt">Executivo</div><div class="pn">Carne assada</div><div class="pd">Arroz, feijão, macaxeira cozida</div></div>
        <div class="pp">R$25</div>
      </div>
      <div class="pc">
        <div><div class="pt">Vegetariano</div><div class="pn">Feijão verde com legumes</div><div class="pd">Arroz integral, salada farta</div></div>
        <div class="pp">R$18</div>
      </div>
      <div class="pc">
        <div><div class="pt">Bebidas</div><div class="pn">Suco natural</div><div class="pd">Acerola, goiaba, caju, tamarindo</div></div>
        <div class="pp">R$6</div>
      </div>
      <div class="pc">
        <div><div class="pt">Sobremesa</div><div class="pn">Doce do dia</div><div class="pd">Consulte o garçom</div></div>
        <div class="pp">R$5</div>
      </div>
    </div>
  </div>

  <!-- MESA -->
  <div id="mesa" class="sec">
    <div class="pad">
      <div class="lbl">Selecione sua mesa</div>
      <div class="mesa-grid">
        <div class="mb ocup" onclick="selMesa(this,1)"><div class="mn">Mesa 1</div><div class="ms">Ocupada</div></div>
        <div class="mb livre" onclick="selMesa(this,2)"><div class="mn">Mesa 2</div><div class="ms">Livre</div></div>
        <div class="mb livre" onclick="selMesa(this,3)"><div class="mn">Mesa 3</div><div class="ms">Livre</div></div>
        <div class="mb ocup" onclick="selMesa(this,4)"><div class="mn">Mesa 4</div><div class="ms">Ocupada</div></div>
        <div class="mb livre" onclick="selMesa(this,5)"><div class="mn">Mesa 5</div><div class="ms">Livre</div></div>
        <div class="mb livre" onclick="selMesa(this,6)"><div class="mn">Mesa 6</div><div class="ms">Livre</div></div>
      </div>
      <div class="cb">
        <div class="cb-titulo"><i class="ti ti-hand-finger" style="color:#0F6E56;margin-right:5px;font-size:16px;vertical-align:-2px"></i>O que precisa?</div>
        <button class="ab" onclick="toast2('Garçom chamado! Aguarde.')"><i class="ti ti-user-check"></i>Chamar garçom</button>
        <button class="ab" onclick="toast2('Pedido de conta enviado!')"><i class="ti ti-receipt"></i>Pedir a conta</button>
        <button class="ab" onclick="toast2('Cardápio físico a caminho!')"><i class="ti ti-clipboard-list"></i>Cardápio físico</button>
      </div>
    </div>
  </div>

  <!-- WHATSAPP -->
  <div id="wpp" class="sec">
    <div class="pad">
      <div class="wpp-hero">
        <div class="wpp-av"><i class="ti ti-brand-whatsapp"></i></div>
        <div><div class="wpp-t">Fale com a gente</div><div class="wpp-s">(75) 99999-0000 · Resp. rápido</div></div>
      </div>
      <a class="gbtn" href="https://wa.me/5575999990000?text=Olá! Vi o cardápio no app e gostaria de fazer um pedido." target="_blank">
        <i class="ti ti-brand-whatsapp" style="vertical-align:-2px;margin-right:6px"></i>Abrir WhatsApp
      </a>
      <div class="lbl">Mensagens rápidas</div>
      <a class="wi" href="https://wa.me/5575999990000?text=Olá! Quero reservar uma mesa para hoje." target="_blank">
        <div><div class="wi-l">Reservar mesa</div><div class="wi-s">Informe horário e número de pessoas</div></div>
        <i class="ti ti-chevron-right"></i>
      </a>
      <a class="wi" href="https://wa.me/5575999990000?text=Olá! Qual o cardápio de hoje?" target="_blank">
        <div><div class="wi-l">Cardápio de hoje</div><div class="wi-s">Receba o cardápio no WhatsApp</div></div>
        <i class="ti ti-chevron-right"></i>
      </a>
      <a class="wi" href="https://wa.me/5575999990000?text=Olá! Gostaria de fazer um pedido para retirada." target="_blank">
        <div><div class="wi-l">Pedido para retirada</div><div class="wi-s">Retire no local sem esperar</div></div>
        <i class="ti ti-chevron-right"></i>
      </a>
      <a class="wi" href="https://wa.me/5575999990000?text=Olá! Qual o horário de funcionamento?" target="_blank">
        <div><div class="wi-l">Horários e informações</div><div class="wi-s">Seg–Sex 11h–15h</div></div>
        <i class="ti ti-chevron-right"></i>
      </a>
    </div>
  </div>

  <!-- FIDELIDADE -->
  <div id="fid" class="sec">
    <div class="pad">
      <div id="toast-fid" class="toast-bar"></div>
      <div class="cartao">
        <div class="ctop">
          <div><div class="cnome">João Silva</div><div class="csub">Membro desde maio 2025</div></div>
          <div class="cnivel" id="f-nivel">Bronze</div>
        </div>
        <div style="display:flex;align-items:baseline">
          <span class="cpts" id="f-pts">7</span>
          <span class="clab">visitas</span>
        </div>
        <div class="bwrap"><div class="bfill" id="f-barra" style="width:70%"></div></div>
        <div class="binfo"><span id="f-blabel">7 de 10 para recompensa</span><span id="f-bpct">70%</span></div>
      </div>
      <div class="lbl" style="margin-top:0">Seu cartão</div>
      <div class="selos" id="selos"></div>
      <div class="rcard">
        <div class="ricon"><i class="ti ti-trophy"></i></div>
        <div><div class="rt" id="f-rtitulo">Faltam 3 visitas</div><div class="rs" id="f-rsub">Complete 10 visitas e ganhe 1 almoço grátis</div></div>
      </div>
      <button class="btnv" onclick="carimbar()"><i class="ti ti-check" style="vertical-align:-2px;margin-right:5px"></i>Registrar visita de hoje</button>
      <button class="btnr" id="btn-res" onclick="resgatar()" disabled><i class="ti ti-gift" style="vertical-align:-2px;margin-right:5px"></i>Resgatar recompensa</button>
      <div class="lbl">Histórico</div>
      <div id="hist"></div>
    </div>
  </div>

  <div class="rodape">Restaurante da Ilha · Paulo Afonso, BA</div>
</div>

<script>
const DIAS=['Domingo','Segunda-feira','Terça-feira','Quarta-feira','Quinta-feira','Sexta-feira','Sábado'];
const MESES=['jan','fev','mar','abr','mai','jun','jul','ago','set','out','nov','dez'];
const PRATOS=['Feijão verde com carne','Frango grelhado','Peixe assado com pirão','Carne de sol','Frango ao molho','Costela no bafo','Feijão verde especial'];
const hoje=new Date();
document.getElementById('hdr-data').textContent=hoje.getDate()+' de '+MESES[hoje.getMonth()]+' de '+hoje.getFullYear();
document.getElementById('dia-pill').textContent=DIAS[hoje.getDay()];
document.getElementById('prato-dia').textContent=PRATOS[hoje.getDay()];

function aba(id,btn){
  document.querySelectorAll('.sec').forEach(s=>s.classList.remove('on'));
  document.querySelectorAll('.nb').forEach(b=>b.classList.remove('on'));
  document.getElementById(id).classList.add('on');
  btn.classList.add('on');
}

let mesaSel=null;
function selMesa(el,n){
  if(el.classList.contains('ocup')){toast2('Mesa '+n+' está ocupada');return;}
  document.querySelectorAll('.mb').forEach(b=>b.classList.remove('sel'));
  el.classList.add('sel');mesaSel=n;
  toast2('Mesa '+n+' selecionada ✓');
}

let _gt;
function toast2(msg){
  const t=document.getElementById('gtoast');
  t.textContent=msg;t.style.display='block';
  clearTimeout(_gt);_gt=setTimeout(()=>t.style.display='none',2600);
}

const META=10;
let vis=7,total=7;
const historico=[
  {t:'g',d:'Visita registrada',dt:'17 mai 2026',p:'+1'},
  {t:'g',d:'Visita registrada',dt:'14 mai 2026',p:'+1'},
  {t:'r',d:'Almoço grátis resgatado',dt:'10 mai 2026',p:'-10'},
  {t:'g',d:'Visita registrada',dt:'08 mai 2026',p:'+1'},
  {t:'g',d:'Visita registrada',dt:'05 mai 2026',p:'+1'},
];

function nivel(v){return v>=50?'Ouro':v>=20?'Prata':'Bronze';}

function renderFid(){
  const pct=Math.round((vis/META)*100);
  document.getElementById('f-pts').textContent=vis;
  document.getElementById('f-nivel').textContent=nivel(total);
  document.getElementById('f-barra').style.width=Math.min(pct,100)+'%';
  document.getElementById('f-blabel').textContent=vis+' de '+META+' para recompensa';
  document.getElementById('f-bpct').textContent=Math.min(pct,100)+'%';
  const falt=META-vis;
  if(vis>=META){
    document.getElementById('f-rtitulo').textContent='Recompensa disponível!';
    document.getElementById('f-rsub').textContent='Você ganhou 1 almoço grátis. Resgate agora!';
    document.getElementById('btn-res').disabled=false;
  } else {
    document.getElementById('f-rtitulo').textContent='Faltam '+falt+' visit'+(falt===1?'a':'as');
    document.getElementById('f-rsub').textContent='Complete '+META+' visitas e ganhe 1 almoço grátis';
    document.getElementById('btn-res').disabled=true;
  }
  const sg=document.getElementById('selos');
  sg.innerHTML='';
  for(let i=0;i<META;i++){
    const d=document.createElement('div');
    if(i===META-1){d.className='selo prm';d.innerHTML='<i class="ti ti-trophy"></i>';}
    else if(i<vis){d.className='selo ok';d.innerHTML='<i class="ti ti-check"></i>';}
    else{d.className='selo vz';d.innerHTML='<i class="ti ti-circle"></i>';}
    sg.appendChild(d);
  }
  const hl=document.getElementById('hist');
  hl.innerHTML='';
  historico.forEach(h=>{
    hl.innerHTML+=`<div class="hist-item"><div style="display:flex;align-items:center;gap:8px"><div class="hav ${h.t}"><i class="ti ${h.t==='g'?'ti-check':'ti-gift'}"></i></div><div><div class="hd">${h.d}</div><div class="hda">${h.dt}</div></div></div><div class="hpt ${h.p.startsWith('+')?'pos':'neg'}">${h.p}</div></div>`;
  });
}

function carimbar(){
  if(vis>=META){toast2('Resgate sua recompensa antes!');return;}
  vis++;total++;
  historico.unshift({t:'g',d:'Visita registrada',dt:'hoje',p:'+1'});
  renderFid();
  toast2(vis>=META?'Parabéns! Recompensa disponível!':'Visita registrada! Faltam '+(META-vis)+' para o prêmio.');
}
function resgatar(){
  if(vis<META)return;
  vis=0;
  historico.unshift({t:'r',d:'Almoço grátis resgatado',dt:'hoje',p:'-10'});
  renderFid();
  toast2('Recompensa resgatada! Bom apetite!');
}

renderFid();
</script>
</body>
</html>
