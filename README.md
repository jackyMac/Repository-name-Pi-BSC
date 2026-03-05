<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Pi BSC | Community Token on BNB Chain</title>
  <meta name="description" content="Pi BSC is a community-powered token on BNB Smart Chain. Buy, verify contract, and view chart." />
  <meta name="theme-color" content="#0b0b2c" />
  <style>
    :root{
      --bg:#07071b;
      --card: rgba(255,255,255,.06);
      --card2: rgba(255,255,255,.09);
      --text: rgba(255,255,255,.92);
      --muted: rgba(255,255,255,.70);
      --line: rgba(255,255,255,.10);
      --gold:#f2c94c;
      --blue:#6ea8fe;
      --green:#2ee59d;
      --shadow: 0 18px 60px rgba(0,0,0,.45);
      --radius: 22px;
      --radius2: 16px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "PingFang SC","Microsoft YaHei", sans-serif;
      color:var(--text);
      background:
        radial-gradient(1000px 600px at 20% 10%, rgba(110,168,254,.18), transparent 55%),
        radial-gradient(900px 500px at 80% 20%, rgba(242,201,76,.16), transparent 55%),
        radial-gradient(900px 700px at 40% 90%, rgba(46,229,157,.12), transparent 60%),
        linear-gradient(180deg, #050514, var(--bg));
      min-height:100vh;
    }
    a{color:inherit; text-decoration:none}
    .wrap{max-width:1120px; margin:0 auto; padding:22px 18px 90px}

    .topbar{
      display:flex; align-items:center; justify-content:space-between; gap:14px;
      position:sticky; top:0; z-index:20;
      padding:14px 10px;
      backdrop-filter: blur(10px);
      background: rgba(7,7,27,.55);
      border-bottom: 1px solid var(--line);
    }
    .brand{display:flex; align-items:center; gap:12px}
    .logo{
      width:40px; height:40px; border-radius:14px;
      background: radial-gradient(circle at 35% 35%, #fff6c2 0%, var(--gold) 35%, rgba(242,201,76,.25) 62%, rgba(110,168,254,.15) 100%);
      box-shadow: 0 10px 30px rgba(242,201,76,.18);
      overflow:hidden;
      display:grid;
      place-items:center;
    }
    .logo img{width:100%; height:100%; object-fit:cover; display:none;}
    .brand h1{margin:0; font-size:16px; letter-spacing:.2px}
    .brand p{margin:0; font-size:12px; color:var(--muted)}
    .nav{display:flex; gap:10px; flex-wrap:wrap; justify-content:flex-end}
    .chip{
      padding:9px 12px;
      border:1px solid var(--line);
      border-radius:999px;
      background: rgba(255,255,255,.04);
      transition: .15s ease;
      font-size:13px;
      color:var(--muted);
    }
    .chip:hover{transform: translateY(-1px); background: rgba(255,255,255,.07); color:var(--text)}

    .hero{
      margin-top:18px;
      border:1px solid var(--line);
      border-radius: var(--radius);
      background: linear-gradient(135deg, rgba(255,255,255,.08), rgba(255,255,255,.03));
      box-shadow: var(--shadow);
      overflow:hidden;
      position:relative;
    }

    /* 1) Banner */
    .banner{
      position:relative;
      height:210px;
      background:
        radial-gradient(900px 260px at 30% 40%, rgba(242,201,76,.22), transparent 60%),
        radial-gradient(900px 260px at 70% 20%, rgba(110,168,254,.18), transparent 60%),
        linear-gradient(135deg, rgba(255,255,255,.04), rgba(0,0,0,.08));
    }
    .banner img{
      position:absolute; inset:0;
      width:100%; height:100%;
      object-fit:cover;
      opacity:.9;
      display:none;
      filter: saturate(1.05) contrast(1.05);
    }
    .banner::after{
      content:"";
      position:absolute; inset:0;
      background: linear-gradient(180deg, rgba(7,7,27,.15), rgba(7,7,27,.85));
    }
    .bannerInner{
      position:absolute; left:18px; right:18px; bottom:18px;
      display:flex; gap:14px; align-items:flex-end; justify-content:space-between;
      z-index:2;
    }
    .titleBlock h2{
      margin:0;
      font-size:34px;
      letter-spacing:-.5px;
      line-height:1.06;
    }
    .titleBlock p{margin:8px 0 0; color:var(--muted); font-size:14px; line-height:1.55; max-width:780px}
    .badge{
      display:inline-flex; gap:8px; align-items:center;
      padding:8px 10px; border-radius:999px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.04);
      color:rgba(255,255,255,.78);
      font-size:12px;
      white-space:nowrap;
    }
    .spark{color:var(--gold)}

    .content{
      padding:18px;
    }

    .grid{
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:16px;
    }
    @media (max-width: 900px){
      .grid{grid-template-columns:1fr}
      .topbar{position:relative}
      .banner{height:240px}
      .bannerInner{flex-direction:column; align-items:flex-start}
      .badge{white-space:normal}
    }

    .subtitle{margin:0 0 14px; color:var(--muted); font-size:15px; line-height:1.6}
    .actions{display:flex; gap:12px; flex-wrap:wrap; margin-top:10px}
    .btn{
      padding:12px 16px;
      border-radius: 14px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.06);
      display:inline-flex; align-items:center; gap:10px;
      transition:.15s ease;
      font-weight:650;
      cursor:pointer;
    }
    .btn:hover{transform: translateY(-1px); background: rgba(255,255,255,.09)}
    .btn.primary{
      background: linear-gradient(135deg, rgba(242,201,76,1), rgba(242,201,76,.78));
      border:0;
      color:#14110a;
      box-shadow: 0 14px 40px rgba(242,201,76,.20);
    }
    .btn.primary:hover{filter:brightness(1.02)}
    .btn .dot{
      width:10px; height:10px; border-radius:999px; background: var(--green);
      box-shadow: 0 0 0 6px rgba(46,229,157,.12);
    }
    .cards{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:12px;
      margin-top:14px;
    }
    @media (max-width: 900px){ .cards{grid-template-columns:1fr} }
    .card{
      padding:14px;
      border-radius: var(--radius2);
      border:1px solid var(--line);
      background: rgba(255,255,255,.05);
    }
    .k{font-size:12px; color:var(--muted); margin:0 0 6px}
    .v{font-size:18px; margin:0}
    .mono{font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace}

    .section{
      margin-top:16px;
      padding:18px;
      border:1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(255,255,255,.04);
    }
    .section h3{margin:0 0 10px; font-size:16px}
    .muted{color:var(--muted)}
    .pill{
      padding:10px 12px;
      border:1px dashed rgba(255,255,255,.20);
      border-radius: 14px;
      background: rgba(0,0,0,.18);
      max-width:100%;
      overflow:auto;
    }
    .copyRow{display:flex; gap:10px; flex-wrap:wrap; align-items:center; margin-top:10px}
    .small{font-size:12px}
    .two{display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-top:12px}
    @media (max-width: 900px){ .two{grid-template-columns:1fr} }

    /* 3) Chart fallback */
    .chartWrap{
      border:1px solid var(--line);
      border-radius: var(--radius);
      overflow:hidden;
      background: rgba(0,0,0,.16);
    }
    iframe{width:100%; height:650px; border:0; display:block}
    .fallback{
      display:none;
      padding:28px 16px;
      text-align:center;
    }
    .fallback p{margin:0 0 12px; color:var(--muted)}
    .toast{
      position:fixed; left:50%; bottom:20px; transform:translateX(-50%);
      padding:10px 12px; border-radius: 999px;
      background: rgba(0,0,0,.65);
      border:1px solid rgba(255,255,255,.14);
      color: rgba(255,255,255,.90);
      display:none;
      z-index:50;
    }

    footer{margin-top:20px; text-align:center; color:rgba(255,255,255,.55); font-size:12px}
    ul{margin:10px 0 0 18px; color:var(--muted); line-height:1.7}
  </style>
</head>

<body>
  <div class="topbar wrap">
    <div class="brand">
      <div class="logo" aria-hidden="true">
        <img id="logoImg" src="assets/logo.png" alt="logo">
      </div>
      <div>
        <h1>Pi BSC</h1>
        <p>Community Token on BNB Smart Chain</p>
      </div>
    </div>
    <div class="nav">
      <a class="chip" href="#token">Token</a>
      <a class="chip" href="#trust">Trust</a>
      <a class="chip" href="#chart">Chart</a>
      <a class="chip" href="#how">How to Buy</a>
    </div>
  </div>

  <div class="wrap">
    <section class="hero">
      <div class="banner">
        <img id="bannerImg" src="assets/banner.png" alt="banner">
        <div class="bannerInner">
          <div class="titleBlock">
            <div class="badge"><span class="spark">◆</span> Clean UI • Mobile • Copy Contract • Chart Fallback</div>
            <h2>Pi BSC Ecosystem</h2>
            <p>
              这是面向社区的 BSC 生态展示页：合约验证、购买入口、信任信息与图表一站式。<br>
              <span class="muted small">提示：BSC 版本属于链上生态资产形态，与 Pi Network 官方主网资产并非同一链原生发行。</span>
            </p>
          </div>
          <div class="badge">CA: <span class="mono" id="badgeCA"></span></div>
        </div>
      </div>

      <div class="content">
        <div class="grid">
          <div>
            <p class="subtitle">
              不整花里胡哨，整能用的：买入入口、合约复制、价格拉取、可信证明链接。<br>
              <span class="muted small">别怕被吐槽丑，我们今天就是来“翻身”的。</span>
            </p>

            <div class="actions">
              <a class="btn primary" id="buyBtn" target="_blank" rel="noreferrer">
                <span class="dot"></span> Buy on PancakeSwap
              </a>
              <a class="btn" id="scanBtn" target="_blank" rel="noreferrer">View on BscScan</a>
              <a class="btn" id="openChartBtn" target="_blank" rel="noreferrer">Open Chart</a>
            </div>

            <div class="cards">
              <div class="card">
                <p class="k">Token</p>
                <p class="v">Pi BSC</p>
              </div>
              <div class="card">
                <p class="k">Chain</p>
                <p class="v">BNB Smart Chain</p>
              </div>
              <div class="card">
                <p class="k">Price (USD)</p>
                <p class="v" id="priceUsd">Loading…</p>
              </div>
            </div>

            <div class="section" id="how">
              <h3>How to Buy</h3>
              <ul>
                <li>钱包切到 BNB Smart Chain，准备 BNB（Gas + 兑换）。</li>
                <li>点击 <b>Buy on PancakeSwap</b> → 粘贴 CA → 选择数量。</li>
                <li>交易失败时，逐步上调滑点（别一次上天）。</li>
                <li>交易前请核验合约、流动性锁定与权限配置。</li>
              </ul>
            </div>
          </div>

          <div>
            <div class="section" id="token">
              <h3>Contract</h3>
              <p class="muted small">合约地址（点击复制）：</p>
              <div class="copyRow">
                <div class="pill mono" id="caText"></div>
                <button class="btn" id="copyBtn" type="button">Copy</button>
              </div>

              <div class="two">
                <div class="card">
                  <p class="k">Total Supply</p>
                  <p class="v">1,000,000,000</p>
                </div>
                <div class="card">
                  <p class="k">Standard</p>
                  <p class="v">BEP-20</p>
                </div>
              </div>

              <p class="muted small" style="margin-top:10px">
                如果你要“正规项目感”，最关键：<b>LP Lock 证明</b>、<b>Ownership 状态</b>、<b>合约开源</b>。
              </p>
            </div>

            <!-- 2) Trust module -->
            <div class="section" id="trust">
              <h3>Trust & Proof</h3>
              <p class="muted small">把“证明链接”放这里，社区看到就安心（没有就会脑补你要跑路）。</p>
              <div class="actions">
                <a class="btn" id="lpProofBtn" target="_blank" rel="noreferrer">LP Locked Proof</a>
                <a class="btn" id="ownerBtn" target="_blank" rel="noreferrer">Ownership Status</a>
                <a class="btn" id="auditBtn" target="_blank" rel="noreferrer">Audit (optional)</a>
                <a class="btn" id="docsBtn" target="_blank" rel="noreferrer">Docs</a>
              </div>
              <p class="muted small" style="margin-top:10px">
                ✅ 你稍后把 LP 锁仓链接 / Renounce 交易哈希 / 审计链接 / 文档链接替换进去就行。
              </p>
            </div>

          </div>
        </div>

        <!-- 3) Chart with fallback -->
        <div class="section" id="chart">
          <h3>Chart</h3>
          <p class="muted small">如果内嵌失败，会自动给你“打开图表”按钮，不再尬住。</p>
          <div class="chartWrap">
            <iframe id="chartFrame" title="chart"></iframe>
            <div class="fallback" id="chartFallback">
              <p>图表内嵌被浏览器拦了（很常见，不是你菜）。</p>
              <a class="btn primary" id="fallbackOpenBtn" target="_blank" rel="noreferrer">
                <span class="dot"></span> Open Chart on Dexscreener
              </a>
            </div>
          </div>
        </div>

        <footer>
          © 2026 Pi BSC Community · Built on BNB Smart Chain · <span class="muted">Clean beats chaos.</span>
        </footer>

      </div>
    </section>
  </div>

  <div class="toast" id="toast">Copied ✅</div>

<script>
  const CA = "0x2c4857ada55b5891014789c0611c7d9b5ea54444";
  const scan = `https://bscscan.com/token/${CA}`;
  const pcs  = `https://pancakeswap.finance/swap?outputCurrency=${CA}`;
  const dex  = `https://dexscreener.com/bsc/${CA}`;

  // banner/logo show if file exists
  const logoImg = document.getElementById("logoImg");
  logoImg.onload = ()=>{ logoImg.style.display="block"; };
  logoImg.onerror= ()=>{ /* keep gradient */ };

  const bannerImg = document.getElementById("bannerImg");
  bannerImg.onload = ()=>{ bannerImg.style.display="block"; };
  bannerImg.onerror= ()=>{ /* keep gradient */ };

  // bind CA display
  document.getElementById("caText").textContent = CA;
  document.getElementById("badgeCA").textContent = CA.slice(0,6) + "…" + CA.slice(-4);

  // bind core links
  document.getElementById("buyBtn").href = pcs;
  document.getElementById("scanBtn").href = scan;
  document.getElementById("openChartBtn").href = dex;

  // TRUST LINKS — 你要替换的就在这里（先给默认）
  // LP Locked Proof: 你锁仓平台（PinkLock/TeamFinance）的锁仓页面链接
  const LP_PROOF = "";      // 例: "https://www.pinksale.finance/pinklock/record/xxxx"
  const OWNER_TX = scan;    // 你如果 Renounce 了，把交易哈希链接放这里: "https://bscscan.com/tx/0x..."
  const AUDIT_URL = "";     // 例: "https://www.certik.com/projects/xxx"
  const DOCS_URL  = "";     // 例: "https://你的文档链接"

  document.getElementById("lpProofBtn").href = LP_PROOF || scan;
  document.getElementById("ownerBtn").href   = OWNER_TX || scan;
  document.getElementById("auditBtn").href   = AUDIT_URL || scan;
  document.getElementById("docsBtn").href    = DOCS_URL || scan;

  // copy CA
  const toast = document.getElementById("toast");
  document.getElementById("copyBtn").addEventListener("click", async () => {
    try{
      await navigator.clipboard.writeText(CA);
    }catch(e){
      const t = document.createElement("textarea");
      t.value = CA; document.body.appendChild(t);
      t.select(); document.execCommand("copy");
      document.body.removeChild(t);
    }
    toast.style.display = "block";
    toast.textContent = "Copied ✅";
    setTimeout(()=>toast.style.display="none", 1200);
  });

  // price via Dexscreener (best-effort)
  async function loadPrice(){
    const el = document.getElementById("priceUsd");
    try{
      const r = await fetch(`https://api.dexscreener.com/latest/dex/tokens/${CA}`);
      const j = await r.json();
      const p = j?.pairs?.[0]?.priceUsd;
      el.textContent = p ? `$${Number(p).toFixed(6)}` : "N/A";
    }catch(e){
      el.textContent = "N/A";
    }
  }
  loadPrice();

  // 3) chart embed + fallback
  const frame = document.getElementById("chartFrame");
  const fallback = document.getElementById("chartFallback");
  const fallbackOpenBtn = document.getElementById("fallbackOpenBtn");
  fallbackOpenBtn.href = dex;

  // Try embed (some browsers block it)
  frame.src = dex;

  // If iframe errors or stays blank too long -> show fallback
  let fired = false;
  const showFallback = () => {
    if (fired) return;
    fired = true;
    frame.style.display = "none";
    fallback.style.display = "block";
  };

  frame.addEventListener("error", showFallback);

  // timeout fallback (in case blocked silently)
  setTimeout(showFallback, 3500);
</script>
</body>
</html>
