<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Thermal Paper Analyzer</title>
<style>
:root{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;color:#20242b;background:#f4f6f8}
*{box-sizing:border-box}body{margin:0;padding:16px;max-width:1100px;margin-inline:auto}
h1{font-size:clamp(1.4rem,4vw,2rem);margin:8px 0 4px}h2{font-size:1.08rem;margin:0 0 12px}
.sub,.note{color:#667085;line-height:1.55}.panel{background:white;border:1px solid #e1e5ea;border-radius:14px;padding:16px;margin:13px 0;box-shadow:0 2px 8px #1720330a}
input[type=file]{max-width:100%;font-size:.9rem}input[type=number]{width:105px;padding:9px;border:1px solid #d0d5dd;border-radius:8px;font-size:1rem}
button{border:0;border-radius:9px;padding:11px 15px;background:#2459a6;color:white;font-weight:650;font-size:.95rem}
button.secondary{background:#edf2f8;color:#26364b}button.danger{background:#fff0f0;color:#a12626}
button:disabled{opacity:.45}
.slot{border:1px solid #e1e5ea;border-radius:11px;padding:12px}
.filename{font-size:.86rem;color:#667085;overflow-wrap:anywhere;margin:8px 0}
.preview img{display:block;max-width:100%;max-height:260px;object-fit:contain;margin:10px auto;border-radius:7px}
.metrics{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px}
.metric{background:#f7f9fc;border-radius:9px;padding:11px;min-width:0}.label{font-size:.78rem;color:#667085}.value{font-size:1.35rem;font-weight:750;font-variant-numeric:tabular-nums;overflow-wrap:anywhere}
.row{display:flex;gap:10px;align-items:center;flex-wrap:wrap}.spacer{flex:1}
.sample{display:grid;grid-template-columns:90px minmax(0,1fr) auto;gap:12px;align-items:center;padding:11px 0;border-bottom:1px solid #edf0f3}
.thumb{width:90px;height:75px;object-fit:contain;background:#f7f9fc;border-radius:7px}
.sample-name{font-size:.9rem;overflow-wrap:anywhere;font-weight:600}.sample-meta{font-size:.8rem;color:#667085;margin-top:4px}
.timebox{display:flex;align-items:center;gap:6px;flex-wrap:wrap;margin-top:7px;font-size:.85rem}
canvas{width:100%;height:auto;display:block}
.legend{display:flex;gap:16px;flex-wrap:wrap;font-size:.85rem;color:#475467;margin:8px 0}
.dot{display:inline-block;width:10px;height:10px;border-radius:50%;margin-right:5px}
.tablewrap{overflow-x:auto}table{border-collapse:collapse;width:100%;font-size:.87rem}th,td{padding:9px 7px;border-bottom:1px solid #edf0f3;text-align:right;white-space:nowrap}th:first-child,td:first-child{text-align:left}
.result{background:#f1f5fa;border-radius:11px;padding:14px;margin-top:12px}
@media(max-width:650px){body{padding:10px}.metrics{grid-template-columns:1fr 1fr}.sample{grid-template-columns:65px minmax(0,1fr)}.thumb{width:65px;height:65px}.sample button{grid-column:2;justify-self:start}}
</style>
</head>
<body>
<header><h1>Thermal Paper Analyzer</h1><div class="sub">感熱紙の平均輝度・RGB値を測定し、時間経過による変化を比較</div></header>

<section class="panel">
<h2>1. 基本状態（実験前）の写真</h2>
<div class="slot">
 <input id="baseFile" type="file" accept="image/*">
 <div id="baseName" class="filename">写真が選択されていません</div>
 <div id="basePreview" class="preview"></div>
 <div class="metrics">
  <div class="metric"><div class="label">平均輝度 Y</div><div class="value" id="baseY">—</div></div>
  <div class="metric"><div class="label">平均 R</div><div class="value" id="baseR">—</div></div>
  <div class="metric"><div class="label">平均 G</div><div class="value" id="baseG">—</div></div>
  <div class="metric"><div class="label">平均 B</div><div class="value" id="baseB">—</div></div>
  <div class="metric"><div class="label">画素数</div><div class="value" id="basePixels">—</div></div>
 </div>
</div>
<p class="note">基本状態の平均輝度を基準（100％）として、実験後の写真を比較します。</p>
</section>

<section class="panel">
<h2>2. 実験後の写真を複数枚読み込む</h2>
<input id="afterFiles" type="file" accept="image/*" multiple>
<p class="note">複数の写真を一度に選択できます。写真ごとに経過時間を入力してください。経過時間は実験開始からの時間（時間単位）です。</p>
<div id="samples"><div class="note">実験後の写真はまだ登録されていません。</div></div>
<div class="row" style="margin-top:12px">
 <button id="sort" class="secondary" disabled>経過時間順に並べ替え</button>
 <button id="csv" disabled>CSVを書き出す</button>
</div>
</section>

<section class="panel">
<h2>3. 時間経過による輝度の変化</h2>
<div class="legend">
 <span><i class="dot" style="background:#2563eb"></i>平均輝度</span>
 <span><i class="dot" style="background:#e07828"></i>輝度残存率（基本状態＝100％）</span>
 <span><i class="dot" style="background:#16966a"></i>輝度減少率</span>
</div>
<canvas id="chart" width="960" height="430"></canvas>
<p class="note">横軸：実験開始からの経過時間（時間）。左縦軸：平均輝度（0～255）。右縦軸：残存率・減少率（％）。点を直線で結びます。</p>
<div class="result" id="latest">基本状態と実験後の写真を登録すると、測定結果が表示されます。</div>
</section>

<section class="panel">
<h2>4. 測定データ一覧</h2>
<div class="tablewrap">
<table><thead><tr><th>区分</th><th>経過時間</th><th>平均輝度</th><th>輝度残存率</th><th>輝度減少率</th><th>平均R</th><th>平均G</th><th>平均B</th></tr></thead>
<tbody id="dataRows"><tr><td colspan="8" style="text-align:center;color:#98a2b3">データがありません</td></tr></tbody></table>
</div>
</section>

<script>
const $=id=>document.getElementById(id);
let baseline=null, samples=[], nextId=1;
const fmt=n=>Number(n).toFixed(2);
function analyze(file){
 return new Promise((resolve,reject)=>{
  const url=URL.createObjectURL(file),img=new Image();
  img.onload=()=>{
   const scale=Math.min(1,5000/Math.max(img.naturalWidth,img.naturalHeight));
   const w=Math.max(1,Math.round(img.naturalWidth*scale)),h=Math.max(1,Math.round(img.naturalHeight*scale));
   const c=document.createElement('canvas');c.width=w;c.height=h;
   const ctx=c.getContext('2d',{willReadFrequently:true});ctx.drawImage(img,0,0,w,h);
   const d=ctx.getImageData(0,0,w,h).data;let sr=0,sg=0,sb=0,sy=0,n=0;
   for(let i=0;i<d.length;i+=4){
    const a=d[i+3]/255;if(a===0)continue;
    const r=d[i]*a+255*(1-a),g=d[i+1]*a+255*(1-a),b=d[i+2]*a+255*(1-a);
    sr+=r;sg+=g;sb+=b;sy+=.299*r+.587*g+.114*b;n++;
   }
   URL.revokeObjectURL(url);
   resolve({name:file.name,y:sy/n,r:sr/n,g:sg/n,b:sb/n,pixels:n,width:img.naturalWidth,height:img.naturalHeight,previewURL:null});
  };
  img.onerror=()=>{URL.revokeObjectURL(url);reject(new Error('画像を読み込めませんでした: '+file.name));};
  img.src=url;
 });
}
function showBaseline(){
 if(!baseline)return;
 $('baseName').textContent=baseline.name+`（${baseline.width} × ${baseline.height} px）`;
 const im=document.createElement('img');im.src=baseline.previewURL;im.alt='基本状態';
 $('basePreview').replaceChildren(im);
 $('baseY').textContent=fmt(baseline.y);$('baseR').textContent=fmt(baseline.r);
 $('baseG').textContent=fmt(baseline.g);$('baseB').textContent=fmt(baseline.b);
 $('basePixels').textContent=baseline.pixels.toLocaleString();
}
$('baseFile').addEventListener('change',async e=>{
 const f=e.target.files?.[0];if(!f)return;
 try{const r=await analyze(f);r.previewURL=URL.createObjectURL(f);if(baseline?.previewURL)URL.revokeObjectURL(baseline.previewURL);baseline=r;showBaseline();update();}
 catch(err){alert(err.message);}
});
$('afterFiles').addEventListener('change',async e=>{
 const files=Array.from(e.target.files||[]);if(!files.length)return;
 for(const f of files){
  try{
   const r=await analyze(f);r.id=nextId++;r.time=samples.length?Math.max(...samples.map(s=>s.time))+1:0;
   r.previewURL=URL.createObjectURL(f);samples.push(r);
  }catch(err){alert(err.message);}
 }
 e.target.value='';renderSamples();update();
});
function renderSamples(){
 const root=$('samples');root.replaceChildren();
 if(!samples.length){root.innerHTML='<div class="note">実験後の写真はまだ登録されていません。</div>';}
 samples.forEach(s=>{
  const wrap=document.createElement('div');wrap.className='sample';
  const im=document.createElement('img');im.className='thumb';im.src=s.previewURL;im.alt='';
  const info=document.createElement('div');
  const name=document.createElement('div');name.className='sample-name';name.textContent=s.name;
  const meta=document.createElement('div');meta.className='sample-meta';meta.textContent=`平均輝度 ${fmt(s.y)} ／ ${s.width} × ${s.height} px`;
  const time=document.createElement('div');time.className='timebox';
  const label=document.createElement('label');label.textContent='経過時間：';
  const input=document.createElement('input');input.type='number';input.min='0';input.step='any';input.value=s.time;input.setAttribute('aria-label',s.name+'の経過時間');
  input.addEventListener('change',()=>{const v=Number(input.value);if(Number.isFinite(v)&&v>=0){s.time=v;update();}else{input.value=s.time;}});
  const unit=document.createElement('span');unit.textContent='時間';
  time.append(label,input,unit);info.append(name,meta,time);
  const del=document.createElement('button');del.className='danger';del.textContent='削除';
  del.addEventListener('click',()=>{URL.revokeObjectURL(s.previewURL);samples=samples.filter(x=>x.id!==s.id);renderSamples();update();});
  wrap.append(im,info,del);root.append(wrap);
 });
 $('sort').disabled=samples.length<2;$('csv').disabled=!baseline||!samples.length;
}
$('sort').addEventListener('click',()=>{samples.sort((a,b)=>a.time-b.time);renderSamples();update();});
function derived(){
 if(!baseline)return [];
 return samples.map(s=>({s,ret:baseline.y===0?null:s.y/baseline.y*100,dec:baseline.y===0?null:(baseline.y-s.y)/baseline.y*100}))
 .sort((a,b)=>a.s.time-b.s.time);
}
function drawChart(){
 const c=$('chart'),ctx=c.getContext('2d'),w=c.width,h=c.height;ctx.clearRect(0,0,w,h);ctx.fillStyle='#fff';ctx.fillRect(0,0,w,h);
 const L=75,R=75,T=35,B=65,pw=w-L-R,ph=h-T-B,pts=derived();
 if(!baseline||!pts.length){ctx.fillStyle='#98a2b3';ctx.font='18px sans-serif';ctx.textAlign='center';ctx.fillText('基本状態と実験後の写真を登録してください',w/2,h/2);return;}
 const maxT=Math.max(1,...pts.map(p=>p.s.time)),minT=Math.min(0,...pts.map(p=>p.s.time));
 const x=t=>L+(t-minT)/(maxT-minT||1)*pw,y=v=>T+ph-v/255*ph,yp=v=>T+ph-v/150*ph;
 ctx.strokeStyle='#e4e7ec';ctx.lineWidth=1;ctx.fillStyle='#667085';ctx.font='13px sans-serif';
 for(let i=0;i<=5;i++){const v=255-i*51,yy=y(v);ctx.beginPath();ctx.moveTo(L,yy);ctx.lineTo(w-R,yy);ctx.stroke();ctx.textAlign='right';ctx.fillText(String(v),L-10,yy+4);ctx.textAlign='left';ctx.fillText(String(i*30),w-R+10,yy+4);}
 ctx.textAlign='center';ctx.fillText('経過時間（時間）',L+pw/2,h-15);
 ctx.save();ctx.translate(18,T+ph/2);ctx.rotate(-Math.PI/2);ctx.fillText('平均輝度（0～255）',0,0);ctx.restore();
 ctx.save();ctx.translate(w-15,T+ph/2);ctx.rotate(Math.PI/2);ctx.fillText('残存率・減少率（％）',0,0);ctx.restore();
 function series(vals,color,scaleY){
  const valid=pts.map((p,i)=>({x:x(p.s.time),v:vals(p),i})).filter(p=>p.v!==null);
  if(!valid.length)return;
  ctx.beginPath();ctx.strokeStyle=color;ctx.lineWidth=3;valid.forEach((p,i)=>{const yy=scaleY(p.v);if(i===0)ctx.moveTo(p.x,yy);else ctx.lineTo(p.x,yy);});ctx.stroke();
  valid.forEach(p=>{ctx.beginPath();ctx.fillStyle=color;ctx.arc(p.x,scaleY(p.v),5,0,Math.PI*2);ctx.fill();});
 }
 series(p=>p.s.y,'#2563eb',y);
 series(p=>p.ret,'#e07828',yp);
 // reduction is shown as a separate line; negative values are allowed, clipped to chart's displayed 0-150% scale.
 series(p=>p.dec,'#16966a',yp);
 ctx.fillStyle='#475467';ctx.font='12px sans-serif';ctx.textAlign='center';
 const ticks=[...new Set([minT,...pts.map(p=>p.s.time),maxT])].sort((a,b)=>a-b);
 ticks.forEach(t=>ctx.fillText(fmt(t).replace(/\.00$/,''),x(t),T+ph+22));
}
function update(){
 drawChart();const rows=$('dataRows');rows.replaceChildren();
 if(!baseline&&!samples.length){rows.innerHTML='<tr><td colspan="8" style="text-align:center;color:#98a2b3">データがありません</td></tr>';}
 else{
  const all=[];
  if(baseline)all.push({label:'基本状態',time:0,y:baseline.y,r:baseline.r,g:baseline.g,b:baseline.b,ret:100,dec:0});
  derived().forEach(p=>all.push({label:p.s.name,time:p.s.time,y:p.s.y,r:p.s.r,g:p.s.g,b:p.s.b,ret:p.ret,dec:p.dec}));
  all.forEach(p=>{
   const tr=document.createElement('tr');
   [p.label,fmt(p.time)+' h',fmt(p.y),p.ret===null?'—':fmt(p.ret)+'％',p.dec===null?'—':fmt(p.dec)+'％',fmt(p.r),fmt(p.g),fmt(p.b)].forEach(v=>{const td=document.createElement('td');td.textContent=v;tr.append(td);});
   rows.append(tr);
  });
 }
 const pts=derived();
 if(!baseline)$('latest').textContent='まず基本状態の写真を登録してください。';
 else if(!pts.length)$('latest').textContent='実験後の写真を登録してください。';
 else{
  const p=pts[pts.length-1],s=p.s;
  $('latest').textContent=`最も経過時間が長い測定（${fmt(s.time)}時間）：平均輝度 ${fmt(s.y)} ／ 輝度残存率 ${p.ret===null?'計算不可':fmt(p.ret)+'％'} ／ 輝度減少率 ${p.dec===null?'計算不可':fmt(p.dec)+'％'}`;
 }
 $('csv').disabled=!baseline||!samples.length;
}
$('csv').addEventListener('click',()=>{
 if(!baseline||!samples.length)return;
 const rows=[['区分','画像名','経過時間（時間）','平均輝度Y','平均R','平均G','平均B','画素数','輝度残存率（％）','輝度減少率（％）']];
 rows.push(['基本状態',baseline.name,0,fmt(baseline.y),fmt(baseline.r),fmt(baseline.g),fmt(baseline.b),baseline.pixels,100,0]);
 derived().forEach(p=>rows.push(['実験後',p.s.name,fmt(p.s.time),fmt(p.s.y),fmt(p.s.r),fmt(p.s.g),fmt(p.s.b),p.s.pixels,p.ret===null?'':fmt(p.ret),p.dec===null?'':fmt(p.dec)]));
 const csv=rows.map(row=>row.map(v=>'"'+String(v).replaceAll('"','""')+'"').join(',')).join('\r\n');
 const blob=new Blob(['\uFEFF'+csv],{type:'text/csv;charset=utf-8;'}),url=URL.createObjectURL(blob);
 const a=document.createElement('a');a.href=url;a.download='thermal_paper_time_series.csv';a.click();URL.revokeObjectURL(url);
});
update();
</script>
</body></html>
