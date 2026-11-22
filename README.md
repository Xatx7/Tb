<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
<meta name="theme-color" content="#3a1a00">
<title>神券阁 · 外卖福利中心</title>
<style>
* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

:root {
  --bg: #FAF0E6;
  --text: #3E2200;
  --text-sub: #9A6B3E;
  --card-bg: #FFFFFF;
  --border: rgba(0,0,0,0.06);
  --shadow: rgba(0,0,0,0.05);
  --tip-bg: linear-gradient(135deg, #FFF3E0, #FFE0B2);
  --float-bg: rgba(255,255,255,0.94);
  --brand: #FF8C00;
}
@media (prefers-color-scheme: dark) {
  :root {
	--bg: #0F0702; --text: #FFE4BA; --text-sub: #C4935A;
	--card-bg: #1E1005; --border: rgba(255,140,0,0.08); --shadow: rgba(0,0,0,0.4);
	--tip-bg: linear-gradient(135deg, #2E1808, #42220A); --float-bg: rgba(18,08,02,0.96);
  }
}

html { scroll-behavior: smooth; }
body {
  background: var(--bg); color: var(--text);
  font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Helvetica Neue", Arial, sans-serif;
  padding-bottom: 100px; min-height: 100vh; overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
}

/* ===== 粒子 ===== */
.particles { position: absolute; inset: 0; overflow: hidden; pointer-events: none; z-index: 0; }
.particle {
  position: absolute; left: 0; bottom: -10px; width: 2px; height: 2px; border-radius: 50%;
  background: transparent;
  box-shadow:
	15vw 0 0 1px rgba(255,210,80,.3), 38vw 8vh 0 0 rgba(255,175,70,.25),
	62vw 4vh 0 1px rgba(255,225,140,.2), 84vw 12vh 0 0 rgba(255,195,90,.25),
	10vw 18vh 0 1px rgba(255,210,80,.18), 50vw 22vh 0 0 rgba(255,185,85,.22),
	28vw 28vh 0 1px rgba(255,220,130,.18), 74vw 32vh 0 0 rgba(255,195,90,.18);
  animation: float-up 8s linear infinite;
}
@keyframes float-up { 0%{transform:translateY(0);opacity:0} 15%{opacity:1} 100%{transform:translateY(-120vh);opacity:0} }
@media (prefers-reduced-motion: reduce) { .particle { animation: none; opacity: .25; } }

/* ===== 头部 ===== */
.hero {
  position: relative; padding: 48px 20px 36px;
  background: linear-gradient(180deg, #0D0500 0%, #3D1A06 52%, #C45200 100%);
  border-radius: 0 0 32px 32px; overflow: hidden;
}
.hero::before {
  content:''; position:absolute; top:-90px; right:-50px; width:240px; height:240px;
  background: radial-gradient(circle, rgba(255,195,75,.2), transparent 68%);
  animation: glow 5s ease-in-out infinite;
}
.hero::after {
  content:''; position:absolute; bottom:-55px; left:-35px; width:190px; height:190px;
  background: radial-gradient(circle, rgba(255,95,0,.15), transparent 68%);
  animation: glow 5s ease-in-out infinite 2.5s;
}
@keyframes glow { 0%,100%{transform:scale(1);opacity:.5} 50%{transform:scale(1.12);opacity:.9} }

.hero-inner { position: relative; z-index: 1; text-align: center; animation: slide-down .55s cubic-bezier(.4,0,.2,1); }
@keyframes slide-down { from{transform:translateY(-16px);opacity:0} to{transform:translateY(0);opacity:1} }

.logo { font-size: 38px; margin-bottom: 6px; filter: drop-shadow(0 2px 12px rgba(255,175,0,.5)); }
.hero h1 {
  font-size: 26px; font-weight: 900; color: #FFF; letter-spacing: 8px; text-indent: 8px;
  text-shadow: 0 2px 18px rgba(255,130,0,.65), 0 0 36px rgba(255,90,0,.25); margin-bottom: 8px;
}
.hero p { font-size: 12px; color: rgba(255,255,255,.5); margin-bottom: 16px; letter-spacing: 2.5px; }

/* 利益点轮播 */
.benefit-wrap { min-height: 20px; margin-bottom: 18px; }
.benefit-text {
  display: inline-block; font-size: 12.5px; color: rgba(255,255,255,.78); font-weight: 600;
  padding: 5px 14px; border-radius: 99px;
  background: rgba(255,255,255,.08); border: 1px solid rgba(255,255,255,.12);
  transition: opacity .25s;
}

/* 链接卡 */
.link-card {
  background: rgba(255,255,255,.06); backdrop-filter: blur(14px); -webkit-backdrop-filter: blur(14px);
  border: 1px solid rgba(255,210,100,.18); border-radius: 14px; padding: 11px 14px;
  margin: 0 auto 14px; max-width: 310px; text-align: left; transition: border-color .25s;
}
.link-card:active { border-color: rgba(255,210,100,.45); }
.link-card-label { font-size: 10.5px; color: rgba(255,255,255,.38); margin-bottom: 3px; }
.link-card-url { font-size: 12px; color: rgba(255,255,255,.78); word-break: break-all; line-height: 1.35; font-family: 'SF Mono', Menlo, monospace; }

/* 主按钮 */
.btn-main {
  display: inline-flex; align-items: center; gap: 7px;
  background: linear-gradient(135deg, #FFD23A, #F28500); color: #4A1A00;
  font-size: 14.5px; font-weight: 800; border: none; border-radius: 28px;
  padding: 12px 30px; cursor: pointer; letter-spacing: .5px;
  box-shadow: 0 6px 20px rgba(255,140,0,.4), inset 0 1px 2px rgba(255,255,255,.45);
  position: relative; overflow: hidden; transition: transform .14s, box-shadow .14s;
}
.btn-main::after {
  content:''; position:absolute; top:0; left:-100%; width:50%; height:100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,.35), transparent);
  transform: skewX(-20deg); animation: shimmer 3.5s infinite;
}
@keyframes shimmer { 0%,60%{left:-100%} 100%{left:200%} }
.btn-main:active { transform: translateY(2px) scale(.97); box-shadow: 0 3px 10px rgba(255,140,0,.25); }
.btn-main.done { background: linear-gradient(135deg,#52C41A,#389E0D); color:#FFF; }

/* 提示条 */
.tip-bar {
  margin: 18px 16px 6px; background: var(--tip-bg); border-radius: 12px; padding: 11px 14px;
  font-size: 12.5px; color: #D45400; font-weight: 700; display: flex; align-items: center; gap: 7px;
  box-shadow: 0 2px 8px var(--shadow); animation: slide-up .45s cubic-bezier(.4,0,.2,1) .12s both;
}

/* ===== 内容 ===== */
.page { padding: 0 16px; }
.section { margin-top: 22px; animation: slide-up .45s cubic-bezier(.4,0,.2,1) both; }
.section:nth-child(1){animation-delay:.06s} .section:nth-child(2){animation-delay:.12s}
.section:nth-child(3){animation-delay:.18s} .section:nth-child(4){animation-delay:.24s}
@keyframes slide-up { from{transform:translateY(12px);opacity:0} to{transform:translateY(0);opacity:1} }

.section-title { display: flex; align-items: center; gap: 9px; margin-bottom: 12px; }
.section-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; box-shadow: 0 0 8px currentColor; }
.section-name { font-size: 15px; font-weight: 900; color: var(--text); letter-spacing: .5px; }
.section-line { flex: 1; height: 1px; background: linear-gradient(90deg,var(--brand,#FF8C00),transparent); opacity: .28; }

/* CPS按钮 */
.cps-btn {
  display: flex; align-items: center; justify-content: space-between;
  border-radius: 16px; padding: 13px 15px; margin-bottom: 10px;
  text-decoration: none; color: #FFF; font-size: 14.5px; font-weight: 700;
  border: 1px solid rgba(255,255,255,.07); position: relative; overflow: hidden;
  box-shadow: 0 3px 12px rgba(0,0,0,.07), inset 0 1px 0 rgba(255,255,255,.12);
  transition: transform .16s cubic-bezier(.4,0,.2,1), box-shadow .16s;
}
.cps-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 22px rgba(0,0,0,.13), inset 0 1px 0 rgba(255,255,255,.14); }
.cps-btn:active { transform: translateY(0) scale(.99); }
.cps-btn::before {
  content:''; position:absolute; top:0; left:0; right:0; height:48%;
  background: linear-gradient(180deg, rgba(255,255,255,.1), transparent);
  border-radius: 16px 16px 0 0; pointer-events:none;
}
.cps-l { display:flex; align-items:center; gap:11px; position:relative; z-index:1; }
.cps-icon {
  width: 36px; height: 36px; border-radius: 11px;
  display:flex; align-items:center; justify-content:center;
  font-size: 17px; background: rgba(255,255,255,.2);
  box-shadow: inset 0 1px 1px rgba(255,255,255,.18), 0 2px 5px rgba(0,0,0,.12);
}
.cps-text { display:flex; flex-direction:column; line-height:1.3; }
.cps-text small { font-size: 10.5px; font-weight: 600; opacity: .75; margin-top:1px; }
.cps-right { display:flex; align-items:center; gap:7px; position:relative; z-index:1; }
.badge-hot {
  font-size: 9.5px; font-weight: 800; padding: 2px 7px; border-radius: 99px;
  background: rgba(0,0,0,.22); color: #FFDF70; border: 1px solid rgba(255,210,80,.4);
}
.cps-arr { font-size: 18px; opacity: .4; transition: transform .2s, opacity .2s; }
.cps-btn:hover .cps-arr { transform: translateX(2px); opacity: .8; }
.cps-btn.opening .cps-arr { animation: spin .7s linear infinite; opacity: .9; }
@keyframes spin { to { transform: rotate(360deg); } }

/* 口令小按钮 */
.cps-code {
  position: relative; z-index: 2; flex-shrink: 0;
  border: 1px solid rgba(255,255,255,.5); background: rgba(255,255,255,.16);
  color: #fff; font-size: 11px; font-weight: 800;
  padding: 5px 10px; border-radius: 99px; cursor: pointer;
  display: flex; align-items: center; gap: 3px;
  backdrop-filter: blur(4px); transition: background .15s, transform .12s;
}
.cps-code:active { transform: scale(.93); background: rgba(255,255,255,.3); }
.cps-code.done { background: #52C41A; border-color: #52C41A; }
.b-mt .cps-code { border-color: rgba(0,0,0,.28); background: rgba(0,0,0,.1); color: #3E2000; }
.b-mt .cps-code.done { background: #2B8A12; border-color: #2B8A12; color: #fff; }

/* 品牌渐变 */
.b-tb   { background: linear-gradient(135deg,#FF8F1F,#E8500A); }
.b-mt   { background: linear-gradient(135deg,#FFD13A,#F0A800); color:#3E2000; }
.b-mtr  { background: linear-gradient(135deg,#FF7043,#D84315); }
.b-ele  { background: linear-gradient(135deg,#3A9BFF,#0D6FE8); }
.b-dp   { background: linear-gradient(135deg,#FF7040,#E53925); }
.b-my   { background: linear-gradient(135deg,#FF5A82,#D81B60); }
.b-ttp  { background: linear-gradient(135deg,#FF8A2B,#F06A00); }
.b-dd   { background: linear-gradient(135deg,#FF8F5E,#F04E1F); }
.b-hotel{ background: linear-gradient(135deg,#FF9D5C,#E8590C); }
.b-flash{ background: linear-gradient(135deg,#FFC93A,#F08A00); color:#3E2000; }

/* 信息卡 */
.info-card {
  background: var(--card-bg); border-radius: 14px; padding: 12px 14px; margin-bottom: 9px;
  border-left: 3px solid var(--brand, #FF8C00); font-size: 12.5px; color: var(--text-sub);
  line-height: 1.75; box-shadow: 0 2px 8px var(--shadow); transition: transform .2s;
}
.info-card:hover { transform: translateX(3px); }
.info-card b { color: var(--text); }

/* ===== 底部 ===== */
.float-bar {
  position: fixed; bottom: 0; left: 0; right: 0; z-index: 100;
  background: var(--float-bg); backdrop-filter: blur(14px); -webkit-backdrop-filter: blur(14px);
  border-top: 1px solid var(--border); padding: 10px 16px max(10px, env(safe-area-inset-bottom));
  display: flex; gap: 9px;
}
.float-btn {
  flex: 1; border: none; border-radius: 14px; padding: 12px; font-size: 13.5px; font-weight: 800;
  cursor: pointer; color: #FFF; box-shadow: 0 4px 12px rgba(255,140,0,.25); transition: transform .14s;
}
.float-btn:active { transform: translateY(2px) scale(.97); }
.float-btn.copy { background: linear-gradient(135deg,#FF8C00,#FF5A00); }
.float-btn.share { background: linear-gradient(135deg,#FFD23A,#F08500); color:#4A1A00; }
.float-btn.done { background: linear-gradient(135deg,#52C41A,#389E0D); color:#FFF; }

/* 回顶 */
.to-top {
  position: fixed; right: 14px; bottom: calc(78px + env(safe-area-inset-bottom)); z-index: 99;
  width: 40px; height: 40px; border-radius: 50%; border: 1px solid var(--border);
  background: var(--card-bg); color: var(--text); font-size: 16px; cursor: pointer;
  box-shadow: 0 3px 12px var(--shadow); opacity: 0; pointer-events: none;
  transform: translateY(8px) scale(.9); transition: all .22s;
}
.to-top.show { opacity: 1; pointer-events: auto; transform: translateY(0) scale(1); }

/* 顶部提示 */
.tip-top {
  position: fixed; top: -56px; left: 50%; transform: translateX(-50%); z-index: 9999;
  background: rgba(0,0,0,.85); color: #FFF; font-size: 13.5px; font-weight: 600;
  padding: 11px 24px; border-radius: 0 0 14px 14px; white-space: nowrap;
  backdrop-filter: blur(8px); transition: top .32s cubic-bezier(.4,0,.2,1);
}
.tip-top.show { top: 0; }

/* 首次引导 */
.guide {
  position: fixed; inset: 0; z-index: 9997; background: rgba(0,0,0,.68);
  display: none; align-items: center; justify-content: center; padding: 20px;
}
.guide.show { display: flex; animation: fade-in .22s; }
@keyframes fade-in { from{opacity:0} to{opacity:1} }
.guide-card {
  background: var(--card-bg); border-radius: 20px; padding: 24px 20px; max-width: 320px; width: 100%;
  text-align: center; box-shadow: 0 16px 40px rgba(0,0,0,.35);
  animation: pop .28s cubic-bezier(.34,1.4,.64,1);
}
@keyframes pop { from{transform:scale(.92);opacity:0} to{transform:scale(1);opacity:1} }
.guide-card h3 { font-size: 17px; color: var(--text); margin-bottom: 14px; }
.guide-step {
  display: flex; align-items: center; gap: 10px; text-align: left;
  background: var(--bg); border-radius: 12px; padding: 10px 12px; margin-bottom: 8px;
  font-size: 13px; color: var(--text-sub);
}
.guide-num {
  width: 24px; height: 24px; border-radius: 50%; flex-shrink: 0;
  background: linear-gradient(135deg,#FF8C00,#FF5A00); color: #FFF;
  display: flex; align-items: center; justify-content: center; font-weight: 800; font-size: 12px;
}
.guide-btn {
  margin-top: 6px; width: 100%; border: none; border-radius: 12px; padding: 13px;
  background: linear-gradient(135deg,#FF8C00,#FF5A00); color: #FFF;
  font-size: 14px; font-weight: 800; cursor: pointer;
}
.guide-skip { display:block; margin-top: 10px; font-size: 12px; color: var(--text-sub); cursor: pointer; }

/* 微信引导 */
.mask {
  position: fixed; inset: 0; background: rgba(0,0,0,.8); z-index: 9998; display: none;
  color: #FFF; text-align: right; padding: 22px; font-size: 14.5px; line-height: 2.2;
}
.mask.show { display: block; animation: fade-in .2s; }
</style>
</head>
<body>

<div class="tip-top" id="tipTop">✅ 链接已复制</div>

<div class="hero">
  <div class="particles"><div class="particle"></div></div>
  <div class="hero-inner">
	<div class="logo">🏮</div>
	<h1>神 券 阁</h1>
	<p>外卖红包 · 到店优惠 · 电影特价 · 打车立减</p>
	<div class="benefit-wrap"><span class="benefit-text" id="benefitText">🔥 今日红包已更新 · 最高可领 20 元</span></div>
	<div class="link-card">
	  <div class="link-card-label">📎 本站地址（复制发给朋友）</div>
	  <div class="link-card-url" id="showUrl"></div>
	</div>
	<button class="btn-main" id="mainCopyBtn" onclick="doCopy(this)">📋 复制本站链接</button>
  </div>
</div>

<div class="tip-bar">🔥 全部官方入口 · 天天可领 · 下单直接减</div>

<div class="page" id="page"></div>

<button class="to-top" id="toTop" onclick="scrollTo({top:0,behavior:'smooth'})">↑</button>

<div class="float-bar">
  <button class="float-btn share" onclick="showMask()">↗ 微信分享</button>
  <button class="float-btn copy" id="floatCopyBtn" onclick="doCopy(this)">📋 复制本站</button>
</div>

<div class="guide" id="guide">
  <div class="guide-card">
	<h3>👋 3步省下一顿饭钱</h3>
	<div class="guide-step"><div class="guide-num">1</div><div>点上面对应红包按钮，跳转平台领券</div></div>
	<div class="guide-step"><div class="guide-num">2</div><div>下单时平台券 + 商家满减 + 支付优惠同时享受</div></div>
	<div class="guide-step"><div class="guide-num">3</div><div>大部分券当天有效，记得及时用掉</div></div>
	<button class="guide-btn" onclick="closeGuide()">知道了，开始省钱</button>
	<span class="guide-skip" onclick="closeGuide()">下次再说</span>
  </div>
</div>

<div class="mask" id="mask" onclick="this.classList.remove('show')">
  <div style="font-size:40px;margin-right:24px">↗</div>
  点右上角「···」→ 复制链接 / 转发朋友
</div>

<script>
/* =========================================================
   配置区 —— 上线前必须替换这5处地址
   ========================================================= */
const CONFIG = {
  invCode: 'xatx6',
  statUrl: '',
  guideKey: 'sqg_guide_v1',
  mtCode: '1来美团，吃得更好，生活更好❤️复制整条信息，打开👉美团👈 http:/💰23OGU4MGQ4NTg💰',   // ← 美团联盟申请
  hotelUrl:  'https://h5.sichuanyunzhan.com/node/entry/Nzv4Gz?templateType=system&entryType=middle&pid=39c606e4ad2b9f9557c0&t=1795315423',
  flashUrl:  'https://h5.sichuanyunzhan.com/node/entry/x4dXB2?templateType=system&entryType=middle&pid=39c606e4ad2b9f9557c0&t=1795315467',
  movieUrl:  'https://1.yoourl.com/link/10000716b026dbf8db9b1000BAY4Tr8X',
  taxiUrl:   'https://h5.sichuanyunzhan.com/node/entry/NBol8y?templateType=system&entryType=middle&pid=39c606e4ad2b9f9557c0&t=1795315385',
};

function esc(s){ return String(s ?? '').replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/'/g,'&#39;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

function getUrl(){
  return 'https://link3.cc/xatx6?from=share&inv=' + encodeURIComponent(CONFIG.invCode);
}
document.getElementById('showUrl').textContent = getUrl().replace(/^https?:\/\//, '');

/* =========================================================
   利益点轮播
   ========================================================= */
const BENEFITS = [
  '🔥 今日红包已更新 · 最高可领 20 元',
  '💰 下单前先在本站领券 · 下单直接减',
  '🛒 淘宝红包天天领 · 下单直接减',
  '🎁 外卖 / 到店 / 电影 / 打车 · 一站全搞定',
  '📋 复制本站链接 · 分享好友一起省'
];
let bIdx = 0, bEl = document.getElementById('benefitText');
if (!window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
  setInterval(() => {
	bEl.style.opacity = '0';
	setTimeout(() => {
	  bIdx = (bIdx + 1) % BENEFITS.length;
	  bEl.textContent = BENEFITS[bIdx];
	  bEl.style.opacity = '1';
	}, 250);
  }, 3200);
}

/* =========================================================
   复制
   ========================================================= */
function vibrate(p){ if(navigator.vibrate) navigator.vibrate(p); }

function doCopy(btn){
  const u = getUrl();
  if (navigator.clipboard && location.protocol === 'https:') {
	navigator.clipboard.writeText(u).then(() => ok(btn,'✅ 链接已复制，快发给朋友吧')).catch(() => fb(u,btn));
  } else { fb(u,btn); }
  track('copy_site');
}
function fb(text,btn){
  const i = document.createElement('input');
  i.value = text; i.style.cssText = 'position:fixed;left:-9999px;opacity:0';
  document.body.appendChild(i); i.select(); i.setSelectionRange(0,99999);
  try { document.execCommand('copy'); ok(btn,'✅ 链接已复制，快发给朋友吧'); }
  catch(e){ showTip('❌ 复制失败，请长按地址栏复制'); }
  document.body.removeChild(i);
}
function ok(btn,msg){
  showTip(msg || '✅ 已复制'); vibrate([40]);
  if(!btn) return;
  const o = btn.innerHTML;
  btn.classList.add('done'); btn.innerHTML = '✅ 已复制';
  setTimeout(() => { btn.classList.remove('done'); btn.innerHTML = o; }, 2000);
}
function showTip(m){
  const t = document.getElementById('tipTop');
  t.textContent = m; t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2400);
}

function copyMtCode(btn){
  event && event.stopPropagation && event.stopPropagation();
  const code = CONFIG.mtCode;
  const done = () => {
	showTip('✅ 口令已复制，打开美团 App 即可领取');
	vibrate([40]);
	const o = btn.innerHTML;
	btn.classList.add('done'); btn.innerHTML = '✅ 已复制';
	setTimeout(() => { btn.classList.remove('done'); btn.innerHTML = o; }, 2200);
	track('copy_mtcode');
  };
  if (navigator.clipboard && location.protocol === 'https:') {
	navigator.clipboard.writeText(code).then(done).catch(() => fbCode(code,done));
  } else { fbCode(code,done); }
}
function fbCode(text,done){
  const i = document.createElement('input');
  i.value = text; i.style.cssText = 'position:fixed;left:-9999px;opacity:0';
  document.body.appendChild(i); i.select(); i.setSelectionRange(0,99999);
  try { document.execCommand('copy'); done(); }
  catch(e){ showTip('❌ 复制失败，请长按口令手动复制'); }
  document.body.removeChild(i);
}

/* =========================================================
   统计
   ========================================================= */
function track(event,label){
  const data = { e:event, l:label||'', t:Date.now(), ref:document.referrer||'' };
  console.log('[神券阁]', data);
  if (CONFIG.statUrl) {
	try { new Image().src = CONFIG.statUrl + '?e=' + encodeURIComponent(data.e) + '&l=' + encodeURIComponent(data.l); } catch(e){}
  }
}

/* =========================================================
   跳转：聚合页新标签，scheme 当前页
   ========================================================= */
function go(el,url,name){
  el.classList.add('opening'); vibrate(20); track('click_'+name,name);
  setTimeout(() => {
	if (/^https?:/i.test(url)) window.open(url,'_blank','noopener');
	else location.href = url;
  }, 260);
}

/* =========================================================
   微信分享 / 引导
   ========================================================= */
function showMask(){ document.getElementById('mask').classList.add('show'); track('share'); }
function closeGuide(){
  document.getElementById('guide').classList.remove('show');
  try { localStorage.setItem(CONFIG.guideKey,'1'); } catch(e){}
}

/* 首次引导弹窗已关闭 —— 如需恢复，删除下方注释块即可
window.addEventListener('load', () => {
  let seen = false;
  try { seen = localStorage.getItem(CONFIG.guideKey) === '1'; } catch(e){}
  if (!seen) setTimeout(() => document.getElementById('guide').classList.add('show'), 800);
});
*/

window.addEventListener('scroll', () => {
  document.getElementById('toTop').classList.toggle('show', window.scrollY > 400);
}, { passive:true });

/* =========================================================
   数据：淘宝第一主推，美团第二（唯一口令位）
   ========================================================= */
const DATA = [
  { section:'🟠 外卖红包', brand:'#FF6A00', items:[
	{ text:'淘宝闪购大红包', sub:'官方入口 · 天天可领', icon:'🛒', cls:'b-tb',
	  url:'https://market.m.taobao.com/app/starlink/wakeup-transit/pages/download?star_id=9249&slk_force_set_request=true&scene=79c3e86933ac4ac6bc1fba486c241ddb', hot:'🔥最热' },
	{ text:'美团外卖大红包', sub:'官方入口 · 天天可领', icon:'🍔', cls:'b-mt',
	  url:'', hasCode:true },
	{ text:'淘宝闪购夜宵专享会场', sub:'夜宵党专属', icon:'🥡', cls:'b-ele',
	  url:'https://market.m.taobao.com/app/starlink/wakeup-transit/pages/download?star_id=8706&slk_force_set_request=true&alsc_exsrc=ES0007485972&scene=a322445b6f6f4252915b185ded0810d7' },
	{ text:'淘宝叠加神券',   sub:'可与红包同用', icon:'🧧', cls:'b-tb',
	  url:'https://market.m.taobao.com/app/starlink/wakeup-transit/pages/download?star_id=8339&slk_force_set_request=true&tfPos=h5&alsc_exsrc=ES0007076172&scene=bb92343302724bb097cf7aac62123654' },
	{ text:'美团外卖大额券', sub:'满减通用 · 秒到账', icon:'🎫', cls:'b-mtr',
	  url:'http://dpurl.cn/6a8iTsmz' },
  ]},
  { section:'🏨 到店优惠', brand:'#FA541C', items:[
	{ text:'酒店集合页', sub:'订房立减 · 新客更优惠', icon:'🏨', cls:'b-hotel', url:CONFIG.hotelUrl },
	{ text:'美团闪购集合页', sub:'超市生鲜红包 · 即时送达', icon:'⚡', cls:'b-flash', url:CONFIG.flashUrl },
  ]},
  { section:'🎬 电影特价', brand:'#722ED1', items:[
	{ text:'电影特价票', sub:'周二周三半价 · 提前买更便宜', icon:'🎬', cls:'b-my', url:CONFIG.movieUrl },
  ]},
  { section:'🚗 打车立减', brand:'#13C2C2', items:[
	{ text:'打车集合页', sub:'聚合补贴 · 通勤天天能用', icon:'🚕', cls:'b-dd', url:CONFIG.taxiUrl },
  ]},
  { tips:[
	'💡 <b>外卖</b>：下单前先在本站领券，平台券 + 商家满减 + 支付优惠可同时享受。',
	'🎬 <b>电影票</b>：周二、周三多为半价日，提前1小时买更便宜。',
	'🚗 <b>打车</b>：高峰前领券，周末平台补贴力度更大。',
	'⏰ <b>红包</b>：大部分券当天有效，记得及时用掉，别等到过期。',
  ]},
];

let h = '';
DATA.forEach(d => {
  if (d.section) {
	h += '<div class="section" style="--brand:' + d.brand + '">'
	  + '<div class="section-title">'
	  + '<div class="section-dot" style="background:' + d.brand + ';color:' + d.brand + '"></div>'
	  + '<div class="section-name">' + d.section + '</div>'
	  + '<div class="section-line"></div></div>';
	d.items.forEach(i => {
	  const badge = i.hot ? '<span class="badge-hot">' + i.hot + '</span>' : '';
	  const codeBtn = i.hasCode
		? '<button class="cps-code" onclick="copyMtCode(this)">🔑 复制口令</button>'
		: '';
	  h += '<a class="cps-btn'+i.CLS + '"href="' + ESC(我。URL) + '"onclick="event.preventDefault()；go(this，\'' + ESC(我。URL) + '\',\'' + ESC(我。文本) + '\')">''<a class="cps-btn'+i.CLS + '"href="' + ESC(我。URL) + '"onclick="event.preventDefault()；go(this，\'' + ESC(我。URL) + '\',\'' + ESC(我。文本) + '\')">'
		+ '<div class="cps-l"><div class="cps-icon">'+i.图标 + '</div>'
		+ '<div class="cps-text">'+i.文本 + '<small>'+i.潜水艇 + '</small></div></div>'
		+ '<div class="cps-right">'+徽章+代码Btn+'<div class="cps-arr">›</div></div>'
		+ '</a>';
	});
H+='</div>';
  }
  如果 (d。提示)d。提示.foreach(t => {H+='<div class="info-card">'+t+'</div>'; });
});
文件。getElementById('页面').innerHTML=h；
</脚本>
</身体>
</超文本标记语言>
