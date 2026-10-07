<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Kin Dee | สั่งอาหารรักสุขภาพ</title>
<!-- โหลดฟอนต์ภาษาไทยจาก Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Thai:wght@400;500&family=Prompt:wght@500;700&display=swap" rel="stylesheet">

<style>
/* ============================================================
   ส่วน CSS (ตกแต่งหน้าตาเว็บ)
   ============================================================ */

/* [CSS-1] ตัวแปรสี: โหมดสว่าง */
:root{--bg:#f2f7ea;--card:#fff;--ink:#17301f;--muted:#5b6e60;--line:#d3e0c8;--leaf:#2c7a46;--lime:#c6e84e;--lime-ink:#17301f;--deep:#143a24;--deep-ink:#eaf5dc;--price:#c4580a;--err:#b3261e;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}

/* [CSS-2] ตัวแปรสี: โหมดมืด (ตามการตั้งค่าเครื่อง) */
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0e1b13;--card:#162a1d;--ink:#e8f3df;--muted:#9bb2a1;--line:#2b4635;--leaf:#6fd08a;--deep:#0a2616;--deep-ink:#e8f3df;--price:#ffa75a;--err:#ff8a80}}
:root[data-theme="dark"]{--bg:#0e1b13;--card:#162a1d;--ink:#e8f3df;--muted:#9bb2a1;--line:#2b4635;--leaf:#6fd08a;--deep:#0a2616;--deep-ink:#e8f3df;--price:#ffa75a;--err:#ff8a80}

/* [CSS-3] พื้นฐานของหน้า: ฟอนต์ สี หัวข้อ */
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:400 16px/1.7 "Noto Sans Thai",system-ui,sans-serif}
h1,h2,h3{font-family:Prompt,"Noto Sans Thai",sans-serif;line-height:1.3;margin:0}
.wrap{max-width:1000px;margin:0 auto;padding:0 20px 120px}

/* [CSS-4] ส่วนหัว: โลโก้ Kin Dee */
header{display:flex;justify-content:space-between;align-items:center;padding:16px 0}
.logo{font:700 1.4rem Prompt,sans-serif;display:flex;align-items:center;gap:8px}
.logo i{width:26px;height:26px;border-radius:50% 50% 50% 4px;background:var(--leaf);display:inline-block}

/* [CSS-5] แถบบอกขั้นตอน 1-5 ด้านบน */
.stepper{display:flex;gap:6px;list-style:none;padding:0;margin:0 0 28px;overflow-x:auto}
.stepper li{flex:1;min-width:84px;border-top:4px solid var(--line);padding-top:6px;font-size:.85rem;color:var(--muted);white-space:nowrap}
.stepper li.done{border-color:var(--leaf);color:var(--ink)}
.stepper li.now{border-color:var(--leaf);color:var(--ink);font-weight:500}
h2{font-size:clamp(1.5rem,3.5vw,2rem)}
.lead{color:var(--muted);margin:6px 0 20px}

/* [CSS-6] ปุ่มและช่องกรอก: สไตล์ปุ่ม + เส้นขอบตอนโฟกัสด้วยคีย์บอร์ด */
.btn{border:0;border-radius:999px;font:500 .95rem "Noto Sans Thai",sans-serif;padding:10px 22px;cursor:pointer;background:var(--lime);color:var(--lime-ink)}
.btn.ghost{background:transparent;border:1.5px solid var(--line);color:var(--ink)}
.btn:disabled{opacity:.45;cursor:not-allowed}
.btn:focus-visible,.chip:focus-visible,summary:focus-visible,input:focus-visible,textarea:focus-visible{outline:3px solid var(--leaf);outline-offset:2px}

/* [CSS-7] ตัวกรองเมนู (ปุ่มกลมๆ: ทั้งหมด / ควบคุมน้ำหนัก ...) */
.chips{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px}
.chip{border:1.5px solid var(--line);background:transparent;color:var(--ink);border-radius:999px;padding:6px 16px;font:inherit;cursor:pointer}
.chip[aria-pressed="true"]{background:var(--deep);color:var(--deep-ink);border-color:var(--deep)}

/* [CSS-8] การ์ดเมนูอาหาร (หน้า 1) */
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:18px}
.dish{background:var(--card);border:1px solid var(--line);border-radius:18px;overflow:hidden;display:flex;flex-direction:column}
.pic{font-size:3.2rem;text-align:center;padding:18px 0;background:color-mix(in srgb,var(--lime) 35%,var(--card))}
.body{padding:14px 16px 16px;display:flex;flex-direction:column;gap:4px;flex:1}
.body h3{font-size:1.05rem}.facts{color:var(--muted);font-size:.9rem}
.foot{display:flex;justify-content:space-between;align-items:center;margin-top:auto;padding-top:10px;gap:8px}
.price{font:700 1.2rem Prompt,sans-serif;color:var(--price)}
.link{background:none;border:0;color:var(--leaf);font:inherit;text-decoration:underline;cursor:pointer;padding:0;text-align:left}

/* [CSS-9] ปุ่มเพิ่ม/ลดจำนวน (+ −) */
.qty{display:inline-flex;align-items:center;gap:10px}
.qty button{width:34px;height:34px;border-radius:50%;border:1.5px solid var(--line);background:var(--card);color:var(--ink);font-size:1.2rem;cursor:pointer}

/* [CSS-10] แถบด้านล่างติดจอ: ยอดรวม + ปุ่มถัดไป/ย้อนกลับ */
.bar{position:fixed;left:0;right:0;bottom:0;background:var(--deep);color:var(--deep-ink);padding:12px 20px calc(12px + env(safe-area-inset-bottom,0px));display:flex;justify-content:space-between;align-items:center;gap:12px}
.bar b{font:700 1.15rem Prompt,sans-serif}

/* [CSS-11] กล่องเนื้อหาและฟอร์ม (หน้า 2: เวลารับ + ที่อยู่) */
.panel{background:var(--card);border:1px solid var(--line);border-radius:18px;padding:20px;margin-bottom:18px}
label.f{display:block;font-weight:500;margin:12px 0 4px}
input[type=text],input[type=tel],textarea{width:100%;font:inherit;color:var(--ink);background:var(--bg);border:1.5px solid var(--line);border-radius:10px;padding:10px 12px}
.err{color:var(--err);font-size:.85rem;min-height:1.2em;margin:2px 0 0}

/* [CSS-12] ตัวเลือกแบบการ์ด (รอบเวลา / วิธีชำระเงิน) */
.opts{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:10px}
.opt{display:flex;gap:10px;align-items:flex-start;border:1.5px solid var(--line);border-radius:12px;padding:12px;cursor:pointer;background:var(--bg)}
.opt:has(input:checked){border-color:var(--leaf);background:color-mix(in srgb,var(--lime) 28%,var(--card))}
.opt small{display:block;color:var(--muted)}

/* [CSS-13] หน้า 3: สรุปออเดอร์และยอดเงิน */
.two{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.sum div{display:flex;justify-content:space-between;padding:3px 0}
.sum .tot{border-top:1px solid var(--line);margin-top:6px;padding-top:8px;font-weight:700}

/* [CSS-14] หน้า 4: ไทม์ไลน์สถานะการจัดส่ง */
.tl{list-style:none;padding:0;margin:0}
.tl li{display:flex;gap:14px;padding:0 0 22px;position:relative;color:var(--muted)}
.tl li::before{content:"";position:absolute;left:13px;top:28px;bottom:0;width:2px;background:var(--line)}
.tl li:last-child::before{display:none}
.tl .dot{flex:none;width:28px;height:28px;border-radius:50%;border:2px solid var(--line);display:grid;place-items:center;font-size:.8rem;background:var(--card)}
.tl li.on{color:var(--ink);font-weight:500}.tl li.on .dot{background:var(--leaf);border-color:var(--leaf);color:#fff}
.tl li.on::before{background:var(--leaf)}

/* [CSS-15] หน้า 5: จัดส่งสำเร็จ */
.big{text-align:center;padding:24px 0}.big .ok{font-size:4rem}

/* [CSS-16] หน้าต่างป็อปอัปรายละเอียดเมนู (ส่วนประกอบ/โภชนาการ) */
dialog{border:0;border-radius:20px;background:var(--card);color:var(--ink);max-width:520px;width:calc(100% - 32px);padding:0}
dialog::backdrop{background:rgba(0,0,0,.5)}
.dlg{padding:22px;max-height:85vh;overflow:auto}
.nut{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin:14px 0;text-align:center}
.nut div{background:var(--bg);border-radius:12px;padding:8px 4px}.nut b{display:block;font:700 1.1rem Prompt,sans-serif}
.nut span{font-size:.8rem;color:var(--muted)}
.dlg ul{margin:6px 0 12px;padding-left:20px}

/* [CSS-17] ปรับสำหรับมือถือ และคนที่ปิดแอนิเมชัน */
@media (max-width:640px){.two{grid-template-columns:1fr}}
@media (prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>

<body>
<!-- ============================================================
     ส่วน HTML (โครงหน้าเว็บ)
     ============================================================ -->
<div class="wrap">
  <!-- [HTML-1] ส่วนหัว: โลโก้ -->
  <header><div class="logo"><i></i>Kin Dee</div><span style="color:var(--muted);font-size:.9rem">อาหารรักสุขภาพ</span></header>
  <!-- [HTML-2] แถบขั้นตอน (JavaScript เติมให้อัตโนมัติ) -->
  <ol class="stepper" id="stp"></ol>
  <!-- [HTML-3] พื้นที่เนื้อหาหลัก (JavaScript เปลี่ยนไปตามแต่ละขั้นตอน) -->
  <main id="app"></main>
</div>
<!-- [HTML-4] ป็อปอัปรายละเอียดเมนู -->
<dialog id="dlg"></dialog>

<script>
/* ============================================================
   ส่วน JavaScript (การทำงานของเว็บ)
   ============================================================ */
(function(){

/* [JS-1] ข้อมูลเมนูอาหาร
   แก้ชื่อ ราคา โภชนาการได้ที่นี่
   id=รหัส n=ชื่อ e=อีโมจิ c=ราคา k=แคลอรี p=โปรตีน cb=คาร์บ f=ไขมัน
   t=หมวด d=คำอธิบาย i=ส่วนประกอบ a=สารก่อภูมิแพ้ */
var MENU=[
{id:1,n:'สลัดอกไก่ย่างน้ำสลัดงา',e:'🥗',c:129,k:320,p:32,cb:14,f:15,t:['protein','diet'],d:'อกไก่ย่างหมักสมุนไพร เสิร์ฟกับผักสดกรอบและน้ำสลัดงาญี่ปุ่นสูตรน้ำตาลน้อย',i:['อกไก่ย่าง','ผักกาดแก้ว','มะเขือเทศเชอรี่','แครอท','ข้าวโพดหวาน','งาขาวคั่ว'],a:'งา, ถั่วเหลือง'},
{id:2,n:'ข้าวกล้องแซลมอนย่างซีอิ๊ว',e:'🍣',c:189,k:480,p:28,cb:52,f:16,t:['protein'],d:'แซลมอนย่างซีอิ๊วญี่ปุ่นเบาเค็ม วางบนข้าวกล้องหอมมะลิพร้อมบร็อกโคลีนึ่ง',i:['แซลมอน','ข้าวกล้อง','บร็อกโคลี','ไข่ต้มยางมะตูม','ขิงดอง'],a:'ปลา, ไข่, ถั่วเหลือง'},
{id:3,n:'โบวล์เต้าหู้ผัดผักรวม',e:'🥦',c:119,k:360,p:18,cb:38,f:14,t:['veg','diet'],d:'เต้าหู้แข็งผัดซอสเต้าเจี้ยวน้อยน้ำมัน กับผักหลากสีและข้าวไรซ์เบอร์รี่',i:['เต้าหู้แข็ง','ข้าวไรซ์เบอร์รี่','เห็ดหอม','พริกหวาน','ถั่วลันเตา','ข้าวโพดอ่อน'],a:'ถั่วเหลือง'},
{id:4,n:'ต้มยำกุ้งน้ำใส ไม่ใส่กะทิ',e:'🍤',c:139,k:210,p:24,cb:12,f:6,t:['protein','diet'],d:'น้ำซุปใสรสจัดจ้านจากข่า ตะไคร้ ใบมะกรูด กุ้งตัวโตและเห็ดฟาง',i:['กุ้งสด','เห็ดฟาง','ข่า','ตะไคร้','ใบมะกรูด','มะเขือเทศ'],a:'กุ้ง (สัตว์น้ำเปลือกแข็ง)'},
{id:5,n:'ซุปฟักทองธัญพืช',e:'🎃',c:99,k:190,p:8,cb:28,f:5,t:['veg','diet'],d:'ซุปฟักทองข้นเนียนจากผักล้วน โรยด้วยธัญพืชอบกรอบ',i:['ฟักทองญี่ปุ่น','หอมใหญ่','นมถั่วเหลือง','เมล็ดฟักทอง','ข้าวโอ๊ต'],a:'ถั่วเหลือง, กลูเตน (ข้าวโอ๊ต)'},
{id:6,n:'ข้าวควินัวผักย่างและเห็ด',e:'🍄',c:129,k:410,p:14,cb:55,f:12,t:['veg'],d:'ควินัวหุงนุ่มกับผักย่างด้วยเตาอบ ราดซอสมะนาวและสมุนไพร',i:['ควินัว','เห็ดออรินจิ','ซูกินี','มะเขือยาว','อะโวคาโด','มะนาว'],a:'ไม่มีสารก่อภูมิแพ้หลัก'}];

/* [JS-2] รอบเวลาจัดส่ง / วิธีชำระเงิน / ขั้นตอนสถานะการส่ง */
var SLOTS=['11:30–12:30','12:30–13:30','17:30–18:30','18:30–19:30'];
var PAY=[{id:'pp',n:'พร้อมเพย์ (QR)',s:'สแกนจ่ายหลังยืนยันออเดอร์'},{id:'card',n:'บัตรเครดิต / เดบิต',s:'Visa, Mastercard, JCB'},{id:'cod',n:'เก็บเงินสดปลายทาง',s:'เตรียมเงินให้พอดี'}];
var STAGES=['รับออเดอร์แล้ว','กำลังปรุงอาหาร','แพ็กใส่กล่องเก็บความเย็น','กำลังนำส่ง','ส่งถึงแล้ว'];

/* [JS-3] สถานะของเว็บ (ขั้นตอนปัจจุบัน ตะกร้า ข้อมูลผู้สั่ง ฯลฯ) */
var S={step:1,cart:{},f:'all',day:'วันนี้',slot:'',pay:'',name:'',tel:'',addr:'',stage:0,no:'',tm:null};
var app=document.getElementById('app'),dlg=document.getElementById('dlg');

/* [JS-4] ฟังก์ชันช่วยคำนวณ: ป้องกันตัวอักษรอันตราย / นับจำนวน / ยอดรวม / ค่าส่ง (ส่งฟรีเมื่อครบ 300) */
function esc(s){var d=document.createElement('div');d.textContent=s;return d.innerHTML}
function cnt(){return Object.keys(S.cart).reduce(function(a,k){return a+S.cart[k]},0)}
function sub(){return Object.keys(S.cart).reduce(function(a,k){return a+S.cart[k]*MENU[k-1].c},0)}
function fee(){return sub()>=300?0:20}
function money(n){return '฿'+n}
function go(n){S.step=n;render();window.scrollTo(0,0)}

/* [JS-5] ชิ้นส่วนหน้าตาที่ใช้ซ้ำ: แถบขั้นตอน / แถบด้านล่าง / ปุ่มเพิ่มลดจำนวน / สรุปออเดอร์ */
function steps(){var L=['เลือกเมนู','เวลารับ','ชำระเงิน','สถานะจัดส่ง','สำเร็จ'];
 document.getElementById('stp').innerHTML=L.map(function(t,i){return '<li class="'+(i+1<S.step?'done':i+1===S.step?'now':'')+'">'+(i+1)+'. '+t+'</li>'}).join('')}
function bar(label,ok,next,back){return '<div class="bar"><div>'+(back?'<button class="btn ghost" data-a="back" style="background:transparent;color:inherit;border-color:rgba(255,255,255,.3)">ย้อนกลับ</button>':'<span>'+cnt()+' รายการ · <b>'+money(sub())+'</b></span>')+'</div><button class="btn" data-a="'+next+'" '+(ok?'':'disabled')+'>'+label+'</button></div>'}
function qtyUI(id){var q=S.cart[id]||0;return q?'<span class="qty"><button data-a="m" data-i="'+id+'" aria-label="ลด">−</button><b>'+q+'</b><button data-a="p" data-i="'+id+'" aria-label="เพิ่ม">+</button></span>':'<button class="btn" data-a="p" data-i="'+id+'">เพิ่ม</button>'}
function summary(){var r=Object.keys(S.cart).map(function(k){var d=MENU[k-1];return '<div><span>'+d.n+' × '+S.cart[k]+'</span><span>'+money(d.c*S.cart[k])+'</span></div>'}).join('');
 return '<div class="sum">'+r+'<div><span>ค่าส่ง'+(fee()?'':' (ส่งฟรีเมื่อครบ 300)')+'</span><span>'+money(fee())+'</span></div><div class="tot"><span>รวมทั้งหมด</span><span>'+money(sub()+fee())+'</span></div></div>'}

/* [JS-6] วาดหน้าเว็บตามขั้นตอน */
function render(){steps();
 if(S.step===1){
  /* ขั้นที่ 1: เลือกเมนู */
  var chips=[['all','ทั้งหมด'],['diet','ควบคุมน้ำหนัก'],['protein','โปรตีนสูง'],['veg','เจ / มังสวิรัติ']].map(function(c){return '<button class="chip" data-a="f" data-f="'+c[0]+'" aria-pressed="'+(S.f===c[0])+'">'+c[1]+'</button>'}).join('');
  var g=MENU.filter(function(d){return S.f==='all'||d.t.indexOf(S.f)>-1}).map(function(d){return '<article class="dish"><div class="pic" aria-hidden="true">'+d.e+'</div><div class="body"><h3>'+d.n+'</h3><div class="facts">'+d.k+' kcal · โปรตีน '+d.p+' g</div><button class="link" data-a="d" data-i="'+d.id+'">ดูส่วนประกอบและโภชนาการ</button><div class="foot"><span class="price">'+money(d.c)+'</span>'+qtyUI(d.id)+'</div></div></article>'}).join('');
  app.innerHTML='<h2>1. เลือกเมนู</h2><p class="lead">กดชื่อเมนูเพื่อดูส่วนประกอบ โภชนาการ และสารก่อภูมิแพ้</p><div class="chips">'+chips+'</div><div class="grid">'+g+'</div>'+bar('ถัดไป: เลือกเวลารับ',cnt()>0,'n2');
 }else if(S.step===2){
  /* ขั้นที่ 2: เลือกเวลารับ + กรอกที่อยู่ */
  var sl=SLOTS.map(function(t){return '<label class="opt"><input type="radio" name="sl" value="'+t+'" '+(S.slot===t?'checked':'')+'><span>'+t+' น.</span></label>'}).join('');
  var dy=['วันนี้','พรุ่งนี้'].map(function(t){return '<label class="opt"><input type="radio" name="dy" value="'+t+'" '+(S.day===t?'checked':'')+'><span>'+t+'</span></label>'}).join('');
  app.innerHTML='<h2>2. เวลาที่จะรับ</h2><p class="lead">เลือกวันและรอบส่ง พร้อมกรอกที่อยู่จัดส่ง</p><div class="panel"><h3>วันและรอบเวลา</h3><div class="opts" style="margin:12px 0">'+dy+'</div><div class="opts">'+sl+'</div><p class="err" id="e-sl"></p></div><div class="panel"><h3>ที่อยู่จัดส่ง</h3><label class="f" for="nm">ชื่อผู้รับ</label><input id="nm" type="text" autocomplete="name" value="'+esc(S.name)+'"><p class="err" id="e-nm"></p><label class="f" for="tl">เบอร์โทร</label><input id="tl" type="tel" autocomplete="tel" value="'+esc(S.tel)+'"><p class="err" id="e-tl"></p><label class="f" for="ad">ที่อยู่</label><textarea id="ad" rows="3" autocomplete="street-address">'+esc(S.addr)+'</textarea><p class="err" id="e-ad"></p></div>'+bar('ถัดไป: ชำระเงิน',true,'n3',true);
 }else if(S.step===3){
  /* ขั้นที่ 3: ตัวเลือกการชำระเงิน + สรุปออเดอร์ */
  var py=PAY.map(function(p){return '<label class="opt"><input type="radio" name="py" value="'+p.id+'" '+(S.pay===p.id?'checked':'')+'><span>'+p.n+'<small>'+p.s+'</small></span></label>'}).join('');
  app.innerHTML='<h2>3. ตัวเลือกการชำระเงิน</h2><p class="lead">ตรวจรายการและเลือกวิธีชำระเงิน</p><div class="two"><div class="panel"><h3>วิธีชำระเงิน</h3><div class="opts" style="grid-template-columns:1fr;margin-top:12px">'+py+'</div><p class="err" id="e-py"></p></div><div class="panel"><h3>สรุปออเดอร์</h3><p style="margin:4px 0 10px;color:var(--muted)">รับ'+S.day+' '+S.slot+' น.<br>'+esc(S.name)+' · '+esc(S.tel)+'</p>'+summary()+'</div></div>'+bar('ยืนยันและสั่งซื้อ',true,'n4',true);
 }else if(S.step===4){
  /* ขั้นที่ 4: สถานะการจัดส่ง (ไทม์ไลน์) */
  var tl=STAGES.map(function(t,i){return '<li class="'+(i<=S.stage?'on':'')+'"><span class="dot">'+(i<=S.stage?'✓':'')+'</span><span>'+t+'</span></li>'}).join('');
  var done=S.stage>=4;
  app.innerHTML='<h2>4. สถานะการจัดส่ง</h2><p class="lead">หมายเลขออเดอร์ <b>'+S.no+'</b> · รับ'+S.day+' '+S.slot+' น.</p><div class="panel"><ol class="tl">'+tl+'</ol></div>'+(done?'<button class="btn" data-a="n5">ดูผลการจัดส่ง</button>':'<p class="lead">หน้านี้อัปเดตสถานะอัตโนมัติ (จำลองตัวอย่าง)</p>');
 }else{
  /* ขั้นที่ 5: จัดส่งสำเร็จ */
  app.innerHTML='<div class="big"><div class="ok" aria-hidden="true">✅</div><h2>5. จัดส่งสำเร็จ</h2><p class="lead">ออเดอร์ '+S.no+' ถึงมือคุณแล้ว ทานให้อร่อยนะ</p></div><div class="panel"><h3>สรุปออเดอร์</h3><p style="margin:4px 0 10px;color:var(--muted)">ส่งที่ '+esc(S.addr)+'</p>'+summary()+'<p class="lead" style="margin:12px 0 0">ชำระด้วย '+PAY.filter(function(p){return p.id===S.pay})[0].n+'</p></div><button class="btn" data-a="again">สั่งอาหารอีกครั้ง</button>';
 }}

/* [JS-7] ป็อปอัปรายละเอียดเมนู: ส่วนประกอบ โภชนาการ สารก่อภูมิแพ้ */
function detail(id){var d=MENU[id-1];
 dlg.innerHTML='<div class="dlg"><div class="pic" style="border-radius:14px;margin-bottom:12px" aria-hidden="true">'+d.e+'</div><h3>'+d.n+'</h3><p style="color:var(--muted);margin:6px 0">'+d.d+'</p><div class="nut"><div><b>'+d.k+'</b><span>kcal</span></div><div><b>'+d.p+' g</b><span>โปรตีน</span></div><div><b>'+d.cb+' g</b><span>คาร์บ</span></div><div><b>'+d.f+' g</b><span>ไขมัน</span></div></div><strong>ส่วนประกอบ</strong><ul>'+d.i.map(function(x){return '<li>'+x+'</li>'}).join('')+'</ul><strong>สารก่อภูมิแพ้</strong><p style="margin:2px 0 14px">'+d.a+'</p><div class="foot"><span class="price">'+money(d.c)+'</span><span style="display:flex;gap:8px;align-items:center">'+qtyUI(id)+'<button class="btn ghost" data-a="x">ปิด</button></span></div></div>';
 if(!dlg.open)dlg.showModal()}

/* [JS-8] ตรวจความถูกต้องของฟอร์มขั้นที่ 2 (รอบเวลา ชื่อ เบอร์โทร ที่อยู่) */
function valid2(){var ok=true;function e(k,t){document.getElementById('e-'+k).textContent=t;if(t)ok=false}
 S.name=document.getElementById('nm').value.trim();S.tel=document.getElementById('tl').value.trim();S.addr=document.getElementById('ad').value.trim();
 var sl=document.querySelector('input[name=sl]:checked');S.slot=sl?sl.value:'';S.day=document.querySelector('input[name=dy]:checked').value;
 e('sl',S.slot?'':'เลือกรอบเวลา');e('nm',S.name?'':'กรอกชื่อผู้รับ');e('tl',/^0\d{8,9}$/.test(S.tel.replace(/[-\s]/g,''))?'':'เบอร์โทรไม่ถูกต้อง เช่น 0812345678');e('ad',S.addr.length>=10?'':'กรอกที่อยู่ให้ละเอียดขึ้น');return ok}

/* [JS-9] จำลองสถานะการจัดส่ง: สร้างเลขออเดอร์ และเลื่อนสถานะทุก 3 วินาที */
function start(){S.stage=0;S.no='KD'+Math.floor(10000+Math.random()*89999);clearInterval(S.tm);
 S.tm=setInterval(function(){if(S.step!==4){clearInterval(S.tm);return}S.stage++;render();if(S.stage>=4)clearInterval(S.tm)},3000)}

/* [JS-10] เพิ่ม/ลดจำนวนสินค้าในตะกร้า */
function change(i,v){S.cart[i]=Math.max(0,(S.cart[i]||0)+v);if(!S.cart[i])delete S.cart[i];render();if(dlg.open)detail(i)}

/* [JS-11] ตัวจับการกดปุ่มทั้งหมด (ดูจาก data-a ของปุ่ม)
   p=เพิ่ม m=ลด f=กรองหมวด d=ดูรายละเอียด x=ปิดป็อปอัป
   n2/n3/n4/n5=ไปขั้นถัดไป back=ย้อนกลับ again=สั่งใหม่ */
document.addEventListener('click',function(e){var b=e.target.closest('[data-a]');if(!b)return;var a=b.dataset.a,i=+b.dataset.i;
 if(a==='p')change(i,1);else if(a==='m')change(i,-1);
 else if(a==='f'){S.f=b.dataset.f;render()}
 else if(a==='d')detail(i);else if(a==='x')dlg.close();
 else if(a==='n2')go(2);
 else if(a==='back')go(S.step-1);
 else if(a==='n3'){if(valid2())go(3)}
 else if(a==='n4'){var p=document.querySelector('input[name=py]:checked');if(!p){document.getElementById('e-py').textContent='เลือกวิธีชำระเงิน';return}S.pay=p.value;start();go(4)}
 else if(a==='n5')go(5);
 else if(a==='again'){S.cart={};S.slot='';S.pay='';go(1)}
});
dlg.addEventListener('click',function(e){if(e.target===dlg)dlg.close()});

/* [JS-12] เริ่มทำงาน: แสดงหน้าแรก */
render();
})();
</script>
</body>
</html>
