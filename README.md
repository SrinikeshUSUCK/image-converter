# image-converter[index.html](https://github.com/user-attachments/files/33875972/index.html)


`<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Image Converter</title>
<meta name="description" content="Convert your images to any format in seconds. Fast, simple, and secure image conversion that runs entirely in your browser.">
<link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 24 24%22><text y=%22.9em%22 font-size=%2222%22>🖼️</text></svg>">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#FAFAF8; --surface:#FFFFFF; --surface-2:#F3F2EE; --border:#E4E2DC;
  --text:#1B1A17; --text-dim:#6B6A64; --text-faint:#A6A49C;
  --accent:#2E6B4E; --accent-hover:#255A40; --accent-soft:#E7F1EC;
  --danger:#B3432B; --danger-soft:#FBEAE5;
  --radius:12px; --radius-sm:8px;
  --shadow:0 1px 2px rgba(20,20,15,.04), 0 4px 14px rgba(20,20,15,.05);
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
  box-sizing:border-box;
}
:root[data-theme="dark"]{
  --bg:#151511; --surface:#1D1C18; --surface-2:#26251F; --border:#37352C;
  --text:#F2F1EC; --text-dim:#A6A49B; --text-faint:#736F64;
  --accent:#4E9C77; --accent-hover:#5EB088; --accent-soft:#20342A;
  --danger:#E07456; --danger-soft:#3A241E;
  --shadow:0 1px 2px rgba(0,0,0,.3), 0 4px 14px rgba(0,0,0,.35);
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){
    --bg:#151511; --surface:#1D1C18; --surface-2:#26251F; --border:#37352C;
    --text:#F2F1EC; --text-dim:#A6A49B; --text-faint:#736F64;
    --accent:#4E9C77; --accent-hover:#5EB088; --accent-soft:#20342A;
    --danger:#E07456; --danger-soft:#3A241E;
    --shadow:0 1px 2px rgba(0,0,0,.3), 0 4px 14px rgba(0,0,0,.35);
  }
}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--text);font-family:Inter,system-ui,-apple-system,sans-serif;-webkit-font-smoothing:antialiased;transition:background .2s,color .2s}
button{font-family:inherit}
h1,h2,h3{margin:0;letter-spacing:-0.02em}
.wrap{max-width:1080px;margin:0 auto;padding:0 20px}
a{color:inherit}

/* header */
header{position:sticky;top:0;z-index:20;background:color-mix(in srgb, var(--bg) 88%, transparent);backdrop-filter:blur(10px);border-bottom:1px solid var(--border);padding-top:env(safe-area-inset-top,0px)}
.hdr-row{display:flex;align-items:center;justify-content:space-between;height:60px}
.brand{display:flex;align-items:center;gap:10px;font-weight:700;font-size:16px}
.brand-mark{width:28px;height:28px;border-radius:8px;background:var(--accent);display:flex;align-items:center;justify-content:center;color:#fff;flex-shrink:0}
nav{display:flex;gap:28px;align-items:center}
nav a{text-decoration:none;color:var(--text-dim);font-size:14px;font-weight:500;cursor:pointer;padding:6px 0;border-bottom:2px solid transparent}
nav a{-webkit-tap-highlight-color:transparent}
nav a:hover{color:var(--text)}
nav a.active{color:var(--text);border-bottom-color:var(--accent)}
nav a:focus-visible{outline:2px solid var(--accent);outline-offset:3px;border-radius:4px}
.hdr-actions{display:flex;gap:8px;align-items:center}
.icon-btn{width:36px;height:36px;border-radius:var(--radius-sm);border:1px solid var(--border);background:var(--surface);display:flex;align-items:center;justify-content:center;cursor:pointer;color:var(--text-dim)}
.icon-btn:hover{background:var(--surface-2);color:var(--text)}
.icon-btn:focus-visible,button:focus-visible,input:focus-visible,select:focus-visible,[tabindex]:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
@media (max-width:720px){
  .hdr-row{flex-wrap:wrap;height:auto;padding:10px 0 8px;row-gap:8px}
  nav{order:3;width:100%;gap:6px}
  nav a{flex:1;text-align:center;padding:8px 6px;border-radius:var(--radius-sm);background:var(--surface-2)}
  nav a.active{background:var(--accent-soft);color:var(--accent)}
}

/* hero */
.hero{padding:44px 0 28px;text-align:left}
.hero h1{font-size:34px;font-weight:800}
.hero p.lead{margin:8px 0 0;font-size:16px;color:var(--text-dim);max-width:480px}
.hero p.sub{margin:10px 0 0;font-size:13.5px;color:var(--text-faint);max-width:520px}

/* upload */
.upload{border:2px dashed var(--border);border-radius:var(--radius);background:var(--surface);padding:44px 20px;text-align:center;transition:border-color .15s, background .15s}
.upload.drag{border-color:var(--accent);background:var(--accent-soft)}
.upload .updicon{width:52px;height:52px;margin:0 auto 14px;color:var(--accent)}
.upload h3{font-size:17px;font-weight:600}
.upload .or{color:var(--text-faint);font-size:13px;margin:10px 0}
.upload-btns{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:6px}
.upload-meta{margin-top:18px;font-size:12.5px;color:var(--text-faint);line-height:1.6}

.btn{border:none;border-radius:var(--radius-sm);padding:10px 18px;font-size:14px;font-weight:600;cursor:pointer;display:inline-flex;align-items:center;gap:8px;transition:background .15s, opacity .15s}
.btn-primary{background:var(--accent);color:#fff}
.btn-primary:hover{background:var(--accent-hover)}
.btn-primary:disabled{opacity:.45;cursor:not-allowed}
.btn-secondary{background:var(--surface);color:var(--text);border:1px solid var(--border)}
.btn-secondary:hover{background:var(--surface-2)}
.btn-ghost{background:transparent;color:var(--text-dim);border:1px solid transparent}
.btn-ghost:hover{color:var(--text);background:var(--surface-2)}
.btn-danger-ghost{background:transparent;color:var(--danger);border:1px solid transparent;font-weight:500}
.btn-danger-ghost:hover{background:var(--danger-soft)}
.btn-block{width:100%;justify-content:center}
.btn-sm{padding:6px 12px;font-size:13px}

/* feature row */
.features{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-top:20px}
.feature{border:1px solid var(--border);background:var(--surface);border-radius:var(--radius-sm);padding:14px;font-size:13px;color:var(--text-dim);display:flex;flex-direction:column;gap:4px}
.feature b{color:var(--text);font-size:13.5px}
@media (max-width:680px){.features{grid-template-columns:1fr 1fr}}

/* main grid once files exist */
.workspace{display:none;grid-template-columns:1.35fr 1fr;gap:24px;margin-top:26px;align-items:start}
.workspace.show{display:grid}
@media (max-width:880px){.workspace.show{grid-template-columns:1fr}}

.panel{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);box-shadow:var(--shadow)}
.panel-head{display:flex;align-items:center;justify-content:space-between;padding:16px 18px;border-bottom:1px solid var(--border)}
.panel-head h2{font-size:15px;font-weight:700}
.panel-body{padding:16px 18px}

/* file list */
.filecard{display:flex;gap:12px;align-items:center;padding:12px 0;border-bottom:1px solid var(--border)}
.filecard:last-child{border-bottom:none}
.thumb{width:48px;height:48px;border-radius:8px;object-fit:cover;background:var(--surface-2);flex-shrink:0;border:1px solid var(--border)}
.finfo{flex:1;min-width:0}
.fname{font-size:13.5px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.fmeta{font-size:12px;color:var(--text-faint);margin-top:2px}
.fstatus{font-size:11.5px;font-weight:600;padding:3px 9px;border-radius:999px;white-space:nowrap}
.fstatus.ready{background:var(--surface-2);color:var(--text-dim)}
.fstatus.converted{background:var(--accent-soft);color:var(--accent)}
.fstatus.failed{background:var(--danger-soft);color:var(--danger)}
.fremove{background:none;border:none;color:var(--text-faint);cursor:pointer;padding:6px;border-radius:6px;flex-shrink:0}
.fremove:hover{color:var(--danger);background:var(--danger-soft)}
.filelist-actions{display:flex;justify-content:space-between;padding:12px 18px;border-top:1px solid var(--border)}

/* settings */
.field{margin-bottom:18px}
.field:last-child{margin-bottom:0}
.field label.flabel{display:block;font-size:13px;font-weight:600;margin-bottom:8px}
select,.numinput{width:100%;padding:9px 10px;border-radius:var(--radius-sm);border:1px solid var(--border);background:var(--bg);color:var(--text);font-size:14px}
.hint{font-size:12px;color:var(--text-faint);margin-top:6px}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.slider-row{display:flex;align-items:center;gap:12px}
input[type=range]{flex:1;accent-color:var(--accent);height:28px}
.sliderval{font-size:13px;font-weight:700;width:34px;text-align:right}
.switch-row{display:flex;align-items:center;justify-content:space-between}
.switch{position:relative;width:42px;height:24px;flex-shrink:0}
.switch input{opacity:0;width:0;height:0}
.slider-track{position:absolute;inset:0;background:var(--border);border-radius:999px;cursor:pointer;transition:.15s}
.slider-track:before{content:"";position:absolute;width:18px;height:18px;left:3px;top:3px;background:#fff;border-radius:50%;transition:.15s}
.switch input:checked + .slider-track{background:var(--accent)}
.switch input:checked + .slider-track:before{transform:translateX(18px)}
.presets{display:flex;flex-wrap:wrap;gap:8px;margin-top:10px}
.preset-chip{border:1px solid var(--border);background:var(--surface);padding:6px 11px;border-radius:999px;font-size:12.5px;cursor:pointer;color:var(--text-dim)}
.preset-chip:hover{border-color:var(--accent);color:var(--text)}
.bgopts{display:flex;gap:8px;margin-top:10px}
.bgopt{width:34px;height:34px;border-radius:8px;border:2px solid var(--border);cursor:pointer;display:flex;align-items:center;justify-content:center}
.bgopt.selected{border-color:var(--accent)}
.bgopt.white{background:#fff}
.bgopt.black{background:#111}
.bgopt.custom input{width:20px;height:20px;border:none;padding:0;background:none;cursor:pointer}

.accordion{border-top:1px solid var(--border);margin-top:18px;padding-top:14px}
.acc-toggle{display:flex;align-items:center;justify-content:space-between;cursor:pointer;font-size:13px;font-weight:600;color:var(--text-dim)}
.acc-body{display:none;margin-top:14px}
.acc-body.open{display:block}
.acc-field{display:flex;align-items:center;justify-content:space-between;padding:8px 0;font-size:13px}
.acc-field .flabel{margin:0;font-weight:500}
.chevron{transition:transform .15s}
.chevron.open{transform:rotate(180deg)}

.convert-bar{padding:16px 18px;border-top:1px solid var(--border)}
.progress-wrap{margin-top:12px}
.progress-track{height:8px;border-radius:999px;background:var(--surface-2);overflow:hidden}
.progress-fill{height:100%;background:var(--accent);width:0%;transition:width .2s}
.progress-label{display:flex;justify-content:space-between;font-size:12.5px;color:var(--text-dim);margin-top:8px}

/* results */
.results-summary{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-bottom:16px}
.results-summary h2{font-size:18px}
.savedpill{background:var(--accent-soft);color:var(--accent);font-size:12.5px;font-weight:700;padding:5px 11px;border-radius:999px}
.resultcard{display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid var(--border)}
.resultcard:last-child{border-bottom:none}
.rinfo{flex:1;min-width:0}
.rname{font-size:13.5px;font-weight:600;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.rmeta{font-size:12px;color:var(--text-faint);margin-top:2px}
.results-actions{display:flex;gap:10px;padding:14px 18px;border-top:1px solid var(--border);flex-wrap:wrap}

.toasts{position:fixed;bottom:20px;right:20px;z-index:50;display:flex;flex-direction:column;gap:10px;max-width:320px}
@media (max-width:600px){.toasts{left:16px;right:16px;bottom:calc(16px + env(safe-area-inset-bottom,0px))}}
.toast{background:var(--surface);border:1px solid var(--border);box-shadow:var(--shadow);border-radius:var(--radius-sm);padding:12px 14px;font-size:13.5px;display:flex;gap:10px;align-items:flex-start;animation:tin .18s ease-out}
.toast.err{border-color:var(--danger)}
@keyframes tin{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

.errbanner{display:flex;gap:10px;align-items:flex-start;background:var(--danger-soft);border:1px solid var(--danger);color:var(--danger);border-radius:var(--radius-sm);padding:12px 14px;font-size:13px;margin-bottom:16px}

footer{margin:60px 0 40px;text-align:center;color:var(--text-faint);font-size:12.5px}
.sr-only{position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0)}
@media (prefers-reduced-motion:reduce){*{animation-duration:0.001ms !important;transition-duration:0.001ms !important}}

.sticky-convert{position:sticky;bottom:0;background:var(--bg);padding:10px 0;display:none}
@media (max-width:880px){.sticky-convert.show{display:block}}

/* ---------- modes, about, extra states ---------- */
[hidden]{display:none !important}
body[data-mode="about"] #uploadSection,
body[data-mode="about"] #featureRow,
body[data-mode="about"] #workspace,
body[data-mode="about"] #resultsPanel{display:none !important}
@media (max-width:720px){ nav a.active{border-bottom-color:transparent} }

.fmeta.err{color:var(--danger);font-weight:500}
.rnote{font-size:12px;color:var(--text-dim);margin-top:3px;line-height:1.4}
.acc-field.disabled{opacity:.5}
.acc-field.disabled *{cursor:not-allowed}
.preset-chip:focus-visible,.acc-toggle:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
.hint a{color:var(--accent)}

.about{padding:44px 0 0}
.about h1{font-size:34px;font-weight:800}
.about .lead{margin:8px 0 22px;font-size:16px;color:var(--text-dim);max-width:600px;line-height:1.5}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px}
@media (max-width:760px){.about-grid{grid-template-columns:1fr}.about h1{font-size:28px}}
.about-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);box-shadow:var(--shadow);padding:20px}
.about-card.wide{margin-bottom:16px}
.about-card h2{font-size:15px;font-weight:700;margin-bottom:10px}
.about-card p,.about-card li{font-size:14px;line-height:1.6;color:var(--text-dim);margin:0}
.about-card ol{margin:0;padding-left:20px;display:grid;gap:8px}
.about-card li b{color:var(--text)}
.about-card a{color:var(--accent);font-weight:600}
.table-scroll{overflow-x:auto;-webkit-overflow-scrolling:touch}
.about table{width:100%;border-collapse:collapse;font-size:13.5px;min-width:520px}
.about th,.about td{text-align:left;padding:10px 12px;border-bottom:1px solid var(--border);vertical-align:top}
.about thead th{font-size:12px;text-transform:uppercase;letter-spacing:.04em;color:var(--text-faint);font-weight:600}
.about tbody th{font-weight:700;color:var(--text);white-space:nowrap}
.about td{color:var(--text-dim)}
.about tbody tr:last-child th,.about tbody tr:last-child td{border-bottom:none}
details{border-bottom:1px solid var(--border);padding:12px 0}
details:last-child{border-bottom:none;padding-bottom:0}
summary{cursor:pointer;font-size:14px;font-weight:600;list-style:none;display:flex;justify-content:space-between;gap:12px}
summary::-webkit-details-marker{display:none}
summary::after{content:"+";color:var(--text-faint);font-weight:500}
details[open] summary::after{content:"\2212"}
details p{margin-top:8px}
summary:focus-visible{outline:2px solid var(--accent);outline-offset:3px;border-radius:4px}

</style>
</head>
<body>

<header>
  <div class="wrap hdr-row">
    <div class="brand">
      <span class="brand-mark" aria-hidden="true">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none"><path d="M4 16l4.5-6 3.5 4.5 2.5-3L20 16" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/><rect x="3" y="4" width="18" height="16" rx="3" stroke="currentColor" stroke-width="2"/></svg>
      </span>
      Image Converter
    </div>
    <nav aria-label="Primary" id="modeNav">
      <a href="#convert" data-mode="convert">Convert</a>
      <a href="#compress" data-mode="compress">Compress</a>
      <a href="#resize" data-mode="resize">Resize</a>
      <a href="#about" data-mode="about">About</a>
    </nav>
    <div class="hdr-actions">
      <button class="icon-btn" id="themeToggle" aria-label="Toggle dark mode" title="Toggle dark mode">
        <svg id="themeIcon" width="17" height="17" viewBox="0 0 24 24" fill="none"><path d="M21 12.4A9 9 0 1111.6 3a7 7 0 009.4 9.4z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/></svg>
      </button>
    </div>
  </div>
</header>

<main class="wrap">
  <section class="hero" id="heroSection">
    <h1 id="heroTitle">Image Converter</h1>
    <p class="lead" id="heroLead">Convert your images to any format in seconds.</p>
    <p class="sub" id="heroSub">Fast, simple, and secure image conversion. Your files are processed locally whenever possible.</p>
  </section>

  <section id="aboutSection" class="about" hidden aria-labelledby="aboutTitle">
    <h1 id="aboutTitle">About Image Converter</h1>
    <p class="lead">A free image tool that does its work inside your browser. Convert, compress and resize pictures without creating an account or uploading anything.</p>

    <div class="about-grid">
      <div class="about-card">
        <h2>How it works</h2>
        <ol>
          <li><b>Add images</b> by dragging them in or choosing files or a folder.</li>
          <li><b>Pick what you need</b>: <a href="#convert">Convert</a> to another format, <a href="#compress">Compress</a> to shrink the file, or <a href="#resize">Resize</a> to change the dimensions.</li>
          <li><b>Press the button</b>, then download one file, all of them, or a single ZIP.</li>
        </ol>
      </div>
      <div class="about-card">
        <h2>Your files stay yours</h2>
        <p>Images are opened and re-encoded on your own device. They are never sent to a server, so there is nothing to sign up for and nothing stored. The only outside request this page makes is loading the Inter font.</p>
      </div>
    </div>

    <div class="about-card wide">
      <h2>Supported formats</h2>
      <div class="table-scroll">
        <table>
          <thead><tr><th scope="col">Format</th><th scope="col">Open</th><th scope="col">Save as</th><th scope="col">Good to know</th></tr></thead>
          <tbody>
            <tr><th scope="row">JPG</th><td>Yes</td><td>Yes</td><td>Best for photos. Has no transparency, so a background colour is used.</td></tr>
            <tr><th scope="row">PNG</th><td>Yes</td><td>Yes</td><td>Lossless with transparency. Compressing PNG rarely saves much.</td></tr>
            <tr><th scope="row">WEBP</th><td>Yes</td><td>Yes</td><td>Smaller than JPG at similar quality. Some browsers can't create it.</td></tr>
            <tr><th scope="row">AVIF</th><td>Yes</td><td>If your browser allows</td><td>If it can't be created here, WEBP is used and you're told.</td></tr>
            <tr><th scope="row">GIF</th><td>Yes</td><td>Yes</td><td>256 colours. Animated GIFs keep only their first frame.</td></tr>
            <tr><th scope="row">BMP</th><td>Yes</td><td>Yes</td><td>Uncompressed, so files are large.</td></tr>
            <tr><th scope="row">TIFF</th><td>Safari only</td><td>Yes</td><td>Uncompressed. Most browsers can't open TIFF files.</td></tr>
            <tr><th scope="row">SVG</th><td>Yes</td><td>Yes</td><td>Your picture is placed inside an SVG file; it isn't turned into vector shapes.</td></tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="about-card wide">
      <h2>Common questions</h2>
      <details><summary>Why didn't my PNG get smaller?</summary><p>PNG is a lossless format, so there is little to remove. For a bigger saving, compress it to WEBP or JPG. If a file can't be made smaller, the original is kept rather than handing you a bigger one.</p></details>
      <details><summary>Is photo metadata (EXIF, location) kept?</summary><p>No. Browsers drop it when an image is re-encoded, which also means shared images don't leak where they were taken.</p></details>
      <details><summary>What are the limits?</summary><p>Each file can be up to 50 MB. Very large dimensions can fail on phones because browsers limit canvas size.</p></details>
      <details><summary>How does resizing treat the aspect ratio?</summary><p>With the lock on, each image is scaled to fit inside the size you set without stretching. Turn the lock off to force exact dimensions.</p></details>
    </div>
  </section>

  <section id="uploadSection" class="upload" tabindex="0" role="button" aria-label="Upload images by clicking or dragging files here">
    <svg class="updicon" viewBox="0 0 24 24" fill="none"><path d="M12 16V4m0 0L7 9m5-5l5 5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/><path d="M4 16v2a2 2 0 002 2h12a2 2 0 002-2v-2" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
    <h3>Drag &amp; drop your images here</h3>
    <div class="or">or</div>
    <div class="upload-btns">
      <button class="btn btn-primary" id="chooseFilesBtn">Choose Images</button>
      <button class="btn btn-secondary" id="chooseFolderBtn">Choose Folder</button>
    </div>
    <div class="upload-meta">
      Supports JPG, JPEG, PNG, WEBP, GIF, BMP, TIFF, SVG, AVIF<br>
      Maximum file size: 50 MB
    </div>
    <input type="file" id="fileInput" class="sr-only" multiple accept="image/*">
    <input type="file" id="folderInput" class="sr-only" multiple webkitdirectory>
  </section>

  <div class="features" id="featureRow">
    <div class="feature"><b>🔒 Private &amp; Secure</b>Files never leave your device</div>
    <div class="feature"><b>⚡ Fast Conversion</b>Runs instantly in your browser</div>
    <div class="feature"><b>📦 Batch Conversion</b>Convert many images at once</div>
    <div class="feature"><b>🖼️ High Quality</b>Fine control over output quality</div>
  </div>

  <div class="workspace" id="workspace">
    <div class="panel" id="filePanel">
      <div class="panel-head">
        <h2 id="fileCountHeading">0 files</h2>
        <button class="btn btn-ghost btn-sm" id="addMoreBtn">+ Add more</button>
      </div>
      <div class="panel-body" id="fileListBody"></div>
      <div class="filelist-actions">
        <button class="btn btn-danger-ghost btn-sm" id="clearAllBtn">Clear all</button>
        <span></span>
      </div>
      <div class="convert-bar">
        <button class="btn btn-primary btn-block" id="convertBtn" disabled>Convert 0 Images</button>
        <div class="progress-wrap" id="progressWrap" style="display:none">
          <div class="progress-track"><div class="progress-fill" id="progressFill"></div></div>
          <div class="progress-label">
            <span id="progressText">Converting…</span>
            <span id="progressPct">0%</span>
          </div>
          <button class="btn btn-ghost btn-sm" id="cancelBtn" style="margin-top:10px">Cancel</button>
        </div>
      </div>
    </div>

    <div class="panel">
      <div class="panel-head"><h2 id="settingsTitle">Conversion settings</h2></div>
      <div class="panel-body">
        <div class="field">
          <label class="flabel" for="formatSelect">Output format</label>
          <select id="formatSelect">
            <option value="original">Same as original</option>
            <option value="jpeg">JPG</option>
            <option value="png" selected>PNG</option>
            <option value="webp">WEBP</option>
            <option value="avif">AVIF</option>
            <option value="gif">GIF</option>
            <option value="bmp">BMP</option>
            <option value="tiff">TIFF</option>
            <option value="svg">SVG</option>
          </select>
          <div class="hint" id="formatHint"></div>
        </div>

        <div class="field" id="qualityField">
          <label class="flabel">Image quality</label>
          <div class="slider-row">
            <input type="range" id="qualitySlider" min="0" max="100" value="85">
            <span class="sliderval" id="qualityVal">85</span>
          </div>
          <div class="hint">Higher quality produces larger files.<span id="qualityHint"></span></div>
        </div>

        <div class="field" id="bgField" style="display:none">
          <label class="flabel">Background color</label>
          <div class="bgopts">
            <div class="bgopt white selected" data-bg="white" title="White"></div>
            <div class="bgopt black" data-bg="black" title="Black"></div>
            <div class="bgopt custom" title="Custom"><input type="color" id="customBg" value="#2E6B4E"></div>
          </div>
        </div>

        <div class="field">
          <div class="switch-row" id="resizeSwitchRow">
            <label class="flabel" for="resizeToggle" style="margin:0">Resize images</label>
            <label class="switch"><input type="checkbox" id="resizeToggle"><span class="slider-track"></span></label>
          </div>
          <div id="resizeBody" style="display:none;margin-top:14px">
            <div class="row2">
              <div>
                <label class="flabel" for="widthInput">Width</label>
                <input class="numinput" type="number" id="widthInput" value="1920" min="1" inputmode="numeric">
              </div>
              <div>
                <label class="flabel" for="heightInput">Height</label>
                <input class="numinput" type="number" id="heightInput" value="1080" min="1" inputmode="numeric">
              </div>
            </div>
            <div class="switch-row" style="margin-top:12px">
              <label class="flabel" for="lockAspect" style="margin:0">Lock aspect ratio</label>
              <label class="switch"><input type="checkbox" id="lockAspect" checked><span class="slider-track"></span></label>
            </div>
            <div class="hint">With the lock on, each image is scaled to fit inside this size without stretching.</div>
            <div class="field" style="margin-top:12px;margin-bottom:0">
              <label class="flabel" for="unitSelect">Unit</label>
              <select id="unitSelect"><option value="px">px</option><option value="%">%</option></select>
            </div>
            <div class="presets" id="presetRow">
              <div class="preset-chip" data-w="0" data-h="0">Original</div>
              <div class="preset-chip" data-w="1920" data-h="1080">1920 × 1080</div>
              <div class="preset-chip" data-w="1280" data-h="720">1280 × 720</div>
              <div class="preset-chip" data-w="1080" data-h="1080">1080 × 1080</div>
              <div class="preset-chip" data-w="800" data-h="600">800 × 600</div>
            </div>
          </div>
        </div>

        <div class="accordion">
          <div class="acc-toggle" id="accToggle">
            Advanced settings
            <svg class="chevron" id="accChevron" width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
          </div>
          <div class="acc-body" id="accBody">
            <div class="acc-field"><label class="flabel" for="metaSelect">Metadata</label>
              <select id="metaSelect" style="width:auto"><option value="strip">Strip metadata</option><option value="preserve">Preserve metadata</option></select>
            </div>
            <div class="acc-field"><span class="flabel">Progressive JPG</span>
              <label class="switch"><input type="checkbox" id="progressiveJpg"><span class="slider-track"></span></label>
            </div>
            <div class="acc-field"><span class="flabel">Preserve transparency</span>
              <label class="switch"><input type="checkbox" id="preserveAlpha" checked><span class="slider-track"></span></label>
            </div>
            <div class="acc-field"><label class="flabel" for="chromaSelect">Chroma subsampling</label>
              <select id="chromaSelect" style="width:auto"><option>4:2:0</option><option>4:2:2</option><option>4:4:4</option></select>
            </div>
            <div class="acc-field"><label class="flabel" for="dpiInput">DPI</label>
              <input class="numinput" id="dpiInput" type="number" value="72" style="width:80px">
            </div>
            <div class="acc-field"><label class="flabel" for="filenamePattern">Filename pattern</label>
              <input class="numinput" id="filenamePattern" type="text" value="{name}" style="width:120px">
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="panel" id="resultsPanel" style="display:none;margin-top:24px">
    <div class="panel-body">
      <div class="results-summary">
        <div>
          <h2 id="resultsTitle">Conversion complete</h2>
          <div class="hint" id="resultsSubtext" style="margin-top:4px"></div>
        </div>
        <span class="savedpill" id="savedPill"></span>
      </div>
      <div id="resultsList"></div>
    </div>
    <div class="results-actions">
      <button class="btn btn-primary" id="downloadAllBtn">Download all</button>
      <button class="btn btn-secondary" id="downloadZipBtn">Download as ZIP</button>
      <button class="btn btn-ghost" id="newConversionBtn">New conversion</button>
    </div>
  </div>

  <footer>Image Converter — conversion runs entirely in your browser. No files are uploaded to any server.</footer>
</main>

<div class="toasts" id="toasts" role="status" aria-live="polite"></div>

<script>

(() => {
  // work/image-converter/src/converter.js
  var EXT = { jpeg: "jpg", png: "png", webp: "webp", avif: "avif", gif: "gif", bmp: "bmp", tiff: "tiff", svg: "svg" };
  var MIME = { jpeg: "image/jpeg", png: "image/png", webp: "image/webp", avif: "image/avif", gif: "image/gif", bmp: "image/bmp", tiff: "image/tiff", svg: "image/svg+xml" };
  var LABEL = { jpeg: "JPG", png: "PNG", webp: "WEBP", avif: "AVIF", gif: "GIF", bmp: "BMP", tiff: "TIFF", svg: "SVG" };
  var ALPHA = /* @__PURE__ */ new Set(["png", "webp", "avif", "gif", "tiff", "svg"]);
  var LOSSY = /* @__PURE__ */ new Set(["jpeg", "webp", "avif"]);
  var FALLBACK = { avif: "webp", webp: "png" };
  function formatFromMime(mime) {
    const m = (mime || "").toLowerCase();
    if (m === "image/jpg" || m === "image/pjpeg") return "jpeg";
    if (m === "image/x-ms-bmp" || m === "image/x-bmp") return "bmp";
    for (const k in MIME) if (MIME[k] === m) return k;
    return null;
  }
  var nativeCache = {};
  function canvasEncodes(mime) {
    if (mime in nativeCache) return nativeCache[mime];
    let ok = false;
    try {
      const c = document.createElement("canvas");
      c.width = c.height = 1;
      ok = c.toDataURL(mime).startsWith("data:" + mime);
    } catch (e) {
    }
    return nativeCache[mime] = ok;
  }
  function loadImage(url) {
    return new Promise((resolve, reject) => {
      const img = new Image();
      img.onload = () => resolve(img);
      img.onerror = () => reject(new Error("load"));
      img.src = url;
    });
  }
  function makeCanvas(w, h) {
    const c = document.createElement("canvas");
    c.width = w;
    c.height = h;
    return c;
  }
  function toBlob(canvas, mime, quality) {
    return new Promise((resolve) => {
      try {
        canvas.toBlob((b) => resolve(b), mime, quality);
      } catch (e) {
        resolve(null);
      }
    });
  }
  function bytesToBase64(bytes) {
    let s = "";
    for (let i = 0; i < bytes.length; i += 32768) s += String.fromCharCode.apply(null, bytes.subarray(i, i + 32768));
    return btoa(s);
  }
  var crcTable = null;
  function crc32(bytes, start = 0, end = bytes.length) {
    if (!crcTable) {
      crcTable = new Uint32Array(256);
      for (let n = 0; n < 256; n++) {
        let c = n;
        for (let k = 0; k < 8; k++) c = c & 1 ? 3988292384 ^ c >>> 1 : c >>> 1;
        crcTable[n] = c >>> 0;
      }
    }
    let crc = 4294967295;
    for (let i = start; i < end; i++) crc = crcTable[(crc ^ bytes[i]) & 255] ^ crc >>> 8;
    return (crc ^ 4294967295) >>> 0;
  }
  function targetSize(nw, nh, opts) {
    if (!opts.resize) return [nw, nh];
    if (opts.unit === "%") {
      const sx = opts.width / 100;
      const sy = opts.lock ? sx : opts.height / 100;
      return [Math.max(1, Math.round(nw * sx)), Math.max(1, Math.round(nh * sy))];
    }
    if (opts.lock) {
      const s = Math.min(opts.width / nw, opts.height / nh);
      return [Math.max(1, Math.round(nw * s)), Math.max(1, Math.round(nh * s))];
    }
    return [Math.round(opts.width), Math.round(opts.height)];
  }
  function drawScaled(img, nw, nh, w, h, bg) {
    let src = img, sw = nw, sh = nh;
    while (sw / 2 >= w && sh / 2 >= h) {
      const tw = Math.max(w, Math.floor(sw / 2));
      const th = Math.max(h, Math.floor(sh / 2));
      const c = makeCanvas(tw, th);
      const cx = c.getContext("2d");
      cx.imageSmoothingEnabled = true;
      cx.imageSmoothingQuality = "high";
      cx.drawImage(src, 0, 0, sw, sh, 0, 0, tw, th);
      src = c;
      sw = tw;
      sh = th;
    }
    const out = makeCanvas(w, h);
    const ctx = out.getContext("2d", { willReadFrequently: true });
    if (bg) {
      ctx.fillStyle = bg;
      ctx.fillRect(0, 0, w, h);
    }
    ctx.imageSmoothingEnabled = true;
    ctx.imageSmoothingQuality = "high";
    ctx.drawImage(src, 0, 0, sw, sh, 0, 0, w, h);
    return out;
  }
  function encodeBMP(imageData, dpi = 72) {
    const { width: w, height: h, data } = imageData;
    const size = 54 + w * h * 4;
    const buf = new ArrayBuffer(size);
    const v = new DataView(buf);
    const ppm = Math.round(dpi / 0.0254);
    v.setUint8(0, 66);
    v.setUint8(1, 77);
    v.setUint32(2, size, true);
    v.setUint32(10, 54, true);
    v.setUint32(14, 40, true);
    v.setInt32(18, w, true);
    v.setInt32(22, h, true);
    v.setUint16(26, 1, true);
    v.setUint16(28, 32, true);
    v.setUint32(30, 0, true);
    v.setUint32(34, w * h * 4, true);
    v.setInt32(38, ppm, true);
    v.setInt32(42, ppm, true);
    const out = new Uint8Array(buf);
    let p = 54;
    for (let y = h - 1; y >= 0; y--) {
      let i = y * w * 4;
      for (let x = 0; x < w; x++, i += 4) {
        out[p++] = data[i + 2];
        out[p++] = data[i + 1];
        out[p++] = data[i];
        out[p++] = data[i + 3];
      }
    }
    return new Blob([buf], { type: MIME.bmp });
  }
  function encodeTIFF(imageData, dpi = 72) {
    const { width: w, height: h, data } = imageData;
    const N = 13, ifdOff = 8, ifdSize = 2 + N * 12 + 4;
    const bpsOff = ifdOff + ifdSize, xrOff = bpsOff + 8, yrOff = xrOff + 8, pixOff = yrOff + 8;
    const total = pixOff + w * h * 4;
    const buf = new ArrayBuffer(total);
    const v = new DataView(buf);
    v.setUint8(0, 73);
    v.setUint8(1, 73);
    v.setUint16(2, 42, true);
    v.setUint32(4, ifdOff, true);
    v.setUint16(ifdOff, N, true);
    let e = ifdOff + 2;
    const entry = (tag, type, count, value) => {
      v.setUint16(e, tag, true);
      v.setUint16(e + 2, type, true);
      v.setUint32(e + 4, count, true);
      if (type === 3 && count === 1) v.setUint16(e + 8, value, true);
      else v.setUint32(e + 8, value, true);
      e += 12;
    };
    entry(256, 4, 1, w);
    entry(257, 4, 1, h);
    entry(258, 3, 4, bpsOff);
    entry(259, 3, 1, 1);
    entry(262, 3, 1, 2);
    entry(273, 4, 1, pixOff);
    entry(277, 3, 1, 4);
    entry(278, 4, 1, h);
    entry(279, 4, 1, w * h * 4);
    entry(282, 5, 1, xrOff);
    entry(283, 5, 1, yrOff);
    entry(296, 3, 1, 2);
    entry(338, 3, 1, 2);
    v.setUint32(e, 0, true);
    for (let i = 0; i < 4; i++) v.setUint16(bpsOff + i * 2, 8, true);
    v.setUint32(xrOff, dpi, true);
    v.setUint32(xrOff + 4, 1, true);
    v.setUint32(yrOff, dpi, true);
    v.setUint32(yrOff + 4, 1, true);
    new Uint8Array(buf, pixOff).set(data);
    return new Blob([buf], { type: MIME.tiff });
  }
  function encodeGIF(imageData) {
    const { width: w, height: h, data } = imageData;
    let hasTrans = false;
    for (let i = 3; i < data.length; i += 4) if (data[i] < 128) {
      hasTrans = true;
      break;
    }
    const TRANS = 255;
    const work = new Float32Array(w * h * 3);
    for (let i = 0, j = 0; i < data.length; i += 4, j += 3) {
      work[j] = data[i];
      work[j + 1] = data[i + 1];
      work[j + 2] = data[i + 2];
    }
    const idx = new Uint8Array(w * h);
    const clamp = (x) => x < 0 ? 0 : x > 255 ? 255 : x;
    const spread = (p, er, eg, eb, f) => {
      work[p] += er * f;
      work[p + 1] += eg * f;
      work[p + 2] += eb * f;
    };
    for (let y = 0; y < h; y++) {
      for (let x = 0; x < w; x++) {
        const px = y * w + x, p = px * 3;
        if (data[px * 4 + 3] < 128) {
          idx[px] = TRANS;
          continue;
        }
        const r = clamp(work[p]), g = clamp(work[p + 1]), b = clamp(work[p + 2]);
        const r3 = Math.round(r / 255 * 7), g3 = Math.round(g / 255 * 7), b2 = Math.round(b / 255 * 3);
        let code = r3 << 5 | g3 << 2 | b2;
        if (hasTrans && code === TRANS) code = 254;
        idx[px] = code;
        const er = r - r3 * 255 / 7, eg = g - g3 * 255 / 7, eb = b - b2 * 255 / 3;
        if (x + 1 < w) spread(p + 3, er, eg, eb, 7 / 16);
        if (y + 1 < h) {
          if (x > 0) spread(p + w * 3 - 3, er, eg, eb, 3 / 16);
          spread(p + w * 3, er, eg, eb, 5 / 16);
          if (x + 1 < w) spread(p + w * 3 + 3, er, eg, eb, 1 / 16);
        }
      }
    }
    const out = [];
    const u16 = (n) => out.push(n & 255, n >> 8 & 255);
    "GIF89a".split("").forEach((c) => out.push(c.charCodeAt(0)));
    u16(w);
    u16(h);
    out.push(247, 0, 0);
    for (let i = 0; i < 256; i++) {
      out.push(Math.round((i >> 5 & 7) * 255 / 7), Math.round((i >> 2 & 7) * 255 / 7), Math.round((i & 3) * 255 / 3));
    }
    if (hasTrans) out.push(33, 249, 4, 1, 0, 0, TRANS, 0);
    out.push(44);
    u16(0);
    u16(0);
    u16(w);
    u16(h);
    out.push(0);
    out.push(8);
    const lzw = lzwEncode(idx, 8);
    for (let i = 0; i < lzw.length; i += 255) {
      const n = Math.min(255, lzw.length - i);
      out.push(n);
      for (let k = 0; k < n; k++) out.push(lzw[i + k]);
    }
    out.push(0, 59);
    return new Blob([Uint8Array.from(out)], { type: MIME.gif });
  }
  function lzwEncode(indices, minSize) {
    const clear = 1 << minSize, eoi = clear + 1;
    const bytes = [];
    let cur = 0, shift = 0, codeSize = minSize + 1, next = eoi + 1;
    let table = /* @__PURE__ */ new Map();
    const emit = (code) => {
      cur |= code << shift;
      shift += codeSize;
      while (shift >= 8) {
        bytes.push(cur & 255);
        cur >>>= 8;
        shift -= 8;
      }
    };
    emit(clear);
    let prefix = indices[0];
    for (let i = 1; i < indices.length; i++) {
      const k = indices[i], key = prefix * 256 + k;
      const found = table.get(key);
      if (found !== void 0) {
        prefix = found;
        continue;
      }
      emit(prefix);
      if (next === 4096) {
        emit(clear);
        table = /* @__PURE__ */ new Map();
        next = eoi + 1;
        codeSize = minSize + 1;
      } else {
        if (next >= 1 << codeSize) codeSize++;
        table.set(key, next++);
      }
      prefix = k;
    }
    emit(prefix);
    emit(eoi);
    if (shift > 0) bytes.push(cur & 255);
    return Uint8Array.from(bytes);
  }
  async function makeZip(files) {
    const enc = new TextEncoder();
    const now = /* @__PURE__ */ new Date();
    const dosTime = now.getHours() << 11 | now.getMinutes() << 5 | now.getSeconds() >> 1;
    const dosDate = now.getFullYear() - 1980 << 9 | now.getMonth() + 1 << 5 | now.getDate();
    const chunks = [], central = [];
    let offset = 0;
    for (const f of files) {
      const data = new Uint8Array(await f.blob.arrayBuffer());
      const name = enc.encode(f.name);
      const crc = crc32(data);
      const lh = new DataView(new ArrayBuffer(30));
      lh.setUint32(0, 67324752, true);
      lh.setUint16(4, 20, true);
      lh.setUint16(6, 2048, true);
      lh.setUint16(8, 0, true);
      lh.setUint16(10, dosTime, true);
      lh.setUint16(12, dosDate, true);
      lh.setUint32(14, crc, true);
      lh.setUint32(18, data.length, true);
      lh.setUint32(22, data.length, true);
      lh.setUint16(26, name.length, true);
      lh.setUint16(28, 0, true);
      chunks.push(new Uint8Array(lh.buffer), name, data);
      const ch = new DataView(new ArrayBuffer(46));
      ch.setUint32(0, 33639248, true);
      ch.setUint16(4, 20, true);
      ch.setUint16(6, 20, true);
      ch.setUint16(8, 2048, true);
      ch.setUint16(10, 0, true);
      ch.setUint16(12, dosTime, true);
      ch.setUint16(14, dosDate, true);
      ch.setUint32(16, crc, true);
      ch.setUint32(20, data.length, true);
      ch.setUint32(24, data.length, true);
      ch.setUint16(28, name.length, true);
      ch.setUint32(42, offset, true);
      central.push(new Uint8Array(ch.buffer), name);
      offset += 30 + name.length + data.length;
    }
    const cdSize = central.reduce((a, c) => a + c.length, 0);
    const end = new DataView(new ArrayBuffer(22));
    end.setUint32(0, 101010256, true);
    end.setUint16(8, files.length, true);
    end.setUint16(10, files.length, true);
    end.setUint32(12, cdSize, true);
    end.setUint32(16, offset, true);
    return new Blob([...chunks, ...central, new Uint8Array(end.buffer)], { type: "application/zip" });
  }
  async function setJpegDpi(blob, dpi) {
    const b = new Uint8Array(await blob.arrayBuffer());
    if (b[2] !== 255 || b[3] !== 224 || b[6] !== 74 || b[7] !== 70) return blob;
    b[13] = 1;
    b[14] = dpi >> 8;
    b[15] = dpi & 255;
    b[16] = dpi >> 8;
    b[17] = dpi & 255;
    return new Blob([b], { type: MIME.jpeg });
  }
  async function setPngDpi(blob, dpi) {
    const b = new Uint8Array(await blob.arrayBuffer());
    const ppm = Math.round(dpi / 0.0254);
    const chunk = new Uint8Array(21);
    const v = new DataView(chunk.buffer);
    v.setUint32(0, 9);
    chunk.set([112, 72, 89, 115], 4);
    v.setUint32(8, ppm);
    v.setUint32(12, ppm);
    chunk[16] = 1;
    v.setUint32(17, crc32(chunk, 4, 17));
    const at = 33;
    const out = new Uint8Array(b.length + chunk.length);
    out.set(b.subarray(0, at), 0);
    out.set(chunk, at);
    out.set(b.subarray(at), at + chunk.length);
    return new Blob([out], { type: MIME.png });
  }
  function resolveFormat(opts, item) {
    if (opts.format !== "original") return opts.format;
    const src = formatFromMime(item.type);
    const map = opts.mode === "compress" ? { jpeg: "jpeg", webp: "webp", avif: "avif", png: "png", bmp: "png", tiff: "png", gif: "png", svg: "png" } : { jpeg: "jpeg", webp: "webp", avif: "avif", png: "png", bmp: "bmp", tiff: "tiff", gif: "png", svg: "png" };
    return map[src] || "png";
  }
  async function convertImage(item, opts) {
    let img;
    try {
      img = await loadImage(item.url);
    } catch (e) {
      return { ok: false, error: "Your browser couldn't open this image." };
    }
    const nw = img.naturalWidth || item.width, nh = img.naturalHeight || item.height;
    if (!nw || !nh) return { ok: false, error: "Couldn't read this image's size." };
    const [w, h] = targetSize(nw, nh, opts);
    if (!(w >= 1) || !(h >= 1)) return { ok: false, error: "Enter a width and height of at least 1." };
    if (w > 16384 || h > 16384 || w * h > 12e7) return { ok: false, error: "That size is too large for your browser." };
    const wanted = resolveFormat(opts, item);
    const flatten = !ALPHA.has(wanted) || !opts.preserveAlpha;
    let canvas;
    try {
      canvas = drawScaled(img, nw, nh, w, h, flatten ? opts.bg : null);
    } catch (e) {
      return { ok: false, error: "This image is too large to process here. Try a smaller size." };
    }
    let blob = null, format = wanted, note = "";
    const dpi = Math.round(opts.dpi) || 72;
    const q = opts.quality / 100;
    try {
      if (wanted === "jpeg" || wanted === "png" || wanted === "webp" || wanted === "avif") {
        format = wanted;
        while (!canvasEncodes(MIME[format]) && FALLBACK[format]) format = FALLBACK[format];
        blob = await toBlob(canvas, MIME[format], LOSSY.has(format) ? q : void 0);
        if (blob && blob.type !== MIME[format] && blob.type === MIME.png) format = "png";
        if (format !== wanted) note = `Your browser can't create ${LABEL[wanted]} files, so ${LABEL[format]} was used instead.`;
        if (blob && dpi !== 72) {
          if (format === "jpeg") blob = await setJpegDpi(blob, dpi);
          else if (format === "png") blob = await setPngDpi(blob, dpi);
        }
      } else if (wanted === "bmp") {
        blob = encodeBMP(canvas.getContext("2d").getImageData(0, 0, w, h), dpi);
      } else if (wanted === "tiff") {
        blob = encodeTIFF(canvas.getContext("2d").getImageData(0, 0, w, h), dpi);
        note = "TIFF files are uncompressed, so they can be large.";
      } else if (wanted === "gif") {
        blob = encodeGIF(canvas.getContext("2d").getImageData(0, 0, w, h));
        note = "GIF uses 256 colours and isn't animated.";
      } else if (wanted === "svg") {
        const png = await toBlob(canvas, MIME.png);
        if (png) {
          const b64 = bytesToBase64(new Uint8Array(await png.arrayBuffer()));
          const href = `data:image/png;base64,${b64}`;
          const svg = `<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="${w}" height="${h}" viewBox="0 0 ${w} ${h}"><image width="${w}" height="${h}" href="${href}" xlink:href="${href}"/></svg>`;
          blob = new Blob([svg], { type: MIME.svg });
          note = "This SVG wraps your image as a picture inside the file; it isn't converted to vector shapes.";
        }
      }
    } catch (e) {
      blob = null;
    }
    if (!blob) return { ok: false, error: "Couldn't convert this image. Try a different output format." };
    const srcFmt = formatFromMime(item.type);
    if (opts.mode === "compress" && !opts.resize && format === srcFmt && ["jpeg", "png", "webp"].includes(format) && blob.size >= item.size) {
      return { ok: true, blob: item.file, format, ext: EXT[format], width: nw, height: nh, kept: true, note: "Already well optimised, so the original was kept." };
    }
    return { ok: true, blob, format, ext: EXT[format], width: w, height: h, note };
  }

  // work/image-converter/src/main.js
  var $ = (s) => document.querySelector(s);
  var $$ = (s) => [...document.querySelectorAll(s)];
  var el = (tag, cls, html) => {
    const e = document.createElement(tag);
    if (cls) e.className = cls;
    if (html !== void 0) e.innerHTML = html;
    return e;
  };
  var esc = (s) => String(s).replace(/[&<>"']/g, (c) => ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" })[c]);
  var state = { mode: null, files: [], results: [], converting: false, cancelRequested: false };
  var MODES = {
    convert: {
      title: "Image Converter",
      lead: "Convert your images to any format in seconds.",
      sub: "Fast, simple, and secure image conversion. Your files are processed locally whenever possible.",
      verb: "Convert",
      ing: "Converting",
      done: "Conversion complete",
      doneNoun: "converted",
      settings: "Conversion settings",
      format: "png",
      quality: 85
    },
    compress: {
      title: "Compress Images",
      lead: "Make your images smaller without losing what matters.",
      sub: "Choose a quality level and shrink your files right in the browser. Nothing is uploaded.",
      verb: "Compress",
      ing: "Compressing",
      done: "Compression complete",
      doneNoun: "compressed",
      settings: "Compression settings",
      format: "original",
      quality: 70
    },
    resize: {
      title: "Resize Images",
      lead: "Change the dimensions of your images in seconds.",
      sub: "Set an exact size or scale by percentage, keeping the aspect ratio intact. Your files never leave your device.",
      verb: "Resize",
      ing: "Resizing",
      done: "Resize complete",
      doneNoun: "resized",
      settings: "Resize settings",
      format: "original",
      quality: 92
    },
    about: { title: "About" }
  };
  var savedSettings = {};
  function modeFromHash() {
    const m = location.hash.replace("#", "").toLowerCase();
    return MODES[m] ? m : "convert";
  }
  $("#themeToggle").addEventListener("click", () => {
    const cur = document.documentElement.getAttribute("data-theme");
    const dark = window.matchMedia("(prefers-color-scheme: dark)").matches;
    const next = cur === "dark" ? "light" : cur === "light" ? "dark" : dark ? "light" : "dark";
    document.documentElement.setAttribute("data-theme", next);
  });
  function toast(msg, type) {
    const t = el("div", "toast" + (type === "err" ? " err" : ""));
    t.textContent = msg;
    $("#toasts").appendChild(t);
    setTimeout(() => {
      t.style.opacity = "0";
      t.style.transition = "opacity .2s";
      setTimeout(() => t.remove(), 200);
    }, type === "err" ? 5e3 : 3200);
  }
  var uploadSection = $("#uploadSection");
  var fileInput = $("#fileInput");
  var folderInput = $("#folderInput");
  $("#chooseFilesBtn").addEventListener("click", (e) => {
    e.stopPropagation();
    fileInput.click();
  });
  $("#chooseFolderBtn").addEventListener("click", (e) => {
    e.stopPropagation();
    folderInput.click();
  });
  uploadSection.addEventListener("click", () => fileInput.click());
  uploadSection.addEventListener("keydown", (e) => {
    if (e.target === uploadSection && (e.key === "Enter" || e.key === " ")) {
      e.preventDefault();
      fileInput.click();
    }
  });
  fileInput.addEventListener("change", (e) => addFiles(e.target.files));
  folderInput.addEventListener("change", (e) => addFiles(e.target.files));
  ["dragenter", "dragover"].forEach((ev) => uploadSection.addEventListener(ev, (e) => {
    e.preventDefault();
    uploadSection.classList.add("drag");
  }));
  ["dragleave", "drop"].forEach((ev) => uploadSection.addEventListener(ev, (e) => {
    e.preventDefault();
    uploadSection.classList.remove("drag");
  }));
  uploadSection.addEventListener("drop", (e) => {
    addFiles(e.dataTransfer.files);
  });
  window.addEventListener("dragover", (e) => e.preventDefault());
  window.addEventListener("drop", (e) => {
    e.preventDefault();
    if (state.mode !== "about" && e.target !== uploadSection && !uploadSection.contains(e.target)) addFiles(e.dataTransfer.files);
  });
  var MAX_SIZE = 50 * 1024 * 1024;
  var EXT_TO_MIME = { jpg: "image/jpeg", jpeg: "image/jpeg", png: "image/png", webp: "image/webp", gif: "image/gif", bmp: "image/bmp", tif: "image/tiff", tiff: "image/tiff", svg: "image/svg+xml", avif: "image/avif" };
  function uid() {
    return crypto.randomUUID ? crypto.randomUUID() : "id-" + Date.now() + "-" + Math.random().toString(16).slice(2);
  }
  function addFiles(fileList) {
    let rejected = 0;
    [...fileList].forEach((f0) => {
      let f = f0;
      if (!f.type) {
        const m = EXT_TO_MIME[(f.name.split(".").pop() || "").toLowerCase()];
        if (m) f = new File([f0], f0.name, { type: m });
      }
      if (!f.type.startsWith("image/")) {
        rejected++;
        return;
      }
      if (f.size > MAX_SIZE) {
        toast(`"${f.name}" is over the 50 MB limit and was skipped.`, "err");
        return;
      }
      const item = {
        id: uid(),
        file: f,
        name: f.name,
        type: f.type,
        size: f.size,
        status: "ready",
        url: URL.createObjectURL(f),
        width: null,
        height: null,
        unreadable: false,
        error: ""
      };
      const img = new Image();
      img.onload = () => {
        item.width = img.naturalWidth;
        item.height = img.naturalHeight;
        if (state.files[0] === item) syncResizeInputs(false);
        renderFileList();
      };
      img.onerror = () => {
        item.status = "failed";
        item.unreadable = true;
        item.error = "Your browser can't open this file.";
        renderFileList();
      };
      img.src = item.url;
      state.files.push(item);
    });
    if (rejected) toast(`${rejected} unsupported file${rejected > 1 ? "s were" : " was"} skipped. Try JPG, PNG, WEBP, GIF, BMP, TIFF, SVG or AVIF.`, "err");
    renderFileList();
    fileInput.value = "";
    folderInput.value = "";
  }
  function fmtSize(bytes) {
    if (bytes < 1024) return bytes + " B";
    if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + " KB";
    return (bytes / 1024 / 1024).toFixed(1) + " MB";
  }
  function extLabel(mime) {
    return (mime.split("/")[1] || "image").replace("svg+xml", "svg").replace("jpeg", "jpg").replace("x-ms-bmp", "bmp").toUpperCase();
  }
  var queue = () => state.files.filter((f) => !f.unreadable);
  function renderFileList() {
    const has = state.files.length > 0;
    $("#workspace").classList.toggle("show", has);
    uploadSection.style.display = has ? "none" : "block";
    $("#featureRow").style.display = has ? "none" : "grid";
    const body = $("#fileListBody");
    body.innerHTML = "";
    state.files.forEach((item) => {
      const card = el("div", "filecard");
      const dims = item.width ? `${item.width} \xD7 ${item.height}` : "\u2026";
      const label = item.status === "ready" ? "Ready" : item.status === "converted" ? "Converted" : "Failed";
      card.innerHTML = `
      <img class="thumb" src="${item.url}" alt="">
      <div class="finfo">
        <div class="fname" title="${esc(item.name)}">${esc(item.name)}</div>
        <div class="fmeta">${extLabel(item.type)} \u2022 ${fmtSize(item.size)} \u2022 ${dims}</div>
        ${item.error ? `<div class="fmeta err">${esc(item.error)}</div>` : ""}
      </div>
      <span class="fstatus ${item.status}">${label}</span>
      <button class="fremove" aria-label="Remove ${esc(item.name)}">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M6 6l12 12M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
      </button>`;
      card.querySelector(".fremove").addEventListener("click", () => removeFile(item.id));
      body.appendChild(card);
    });
    $("#fileCountHeading").textContent = `${state.files.length} file${state.files.length === 1 ? "" : "s"}`;
    updateConvertButton();
  }
  function updateConvertButton() {
    const n = queue().length;
    const btn = $("#convertBtn");
    const verb = MODES[state.mode] && MODES[state.mode].verb || "Convert";
    btn.disabled = n === 0 || state.converting;
    btn.textContent = `${verb} ${n} Image${n === 1 ? "" : "s"}`;
  }
  function removeFile(id) {
    const idx = state.files.findIndex((f) => f.id === id);
    if (idx > -1) {
      URL.revokeObjectURL(state.files[idx].url);
      state.files.splice(idx, 1);
      state.results = state.results.filter((r) => r.id !== id);
      if (!state.results.length) $("#resultsPanel").style.display = "none";
      renderFileList();
    }
  }
  $("#clearAllBtn").addEventListener("click", () => {
    state.files.forEach((f) => URL.revokeObjectURL(f.url));
    state.files = [];
    state.results = [];
    $("#resultsPanel").style.display = "none";
    renderFileList();
  });
  $("#addMoreBtn").addEventListener("click", () => fileInput.click());
  var formatSelect = $("#formatSelect");
  var qualitySlider = $("#qualitySlider");
  var qualityVal = $("#qualityVal");
  var resizeToggle = $("#resizeToggle");
  var widthInput = $("#widthInput");
  var heightInput = $("#heightInput");
  var lockAspect = $("#lockAspect");
  var unitSelect = $("#unitSelect");
  var preserveAlpha = $("#preserveAlpha");
  var ALPHA_FORMATS = ["png", "webp", "gif", "avif", "tiff", "svg"];
  var QUALITY_FORMATS = ["jpeg", "webp", "avif"];
  var FORMAT_HINTS = {
    original: "Each image keeps its own format.",
    avif: "Not every browser can create AVIF. If yours can't, WEBP is used instead.",
    gif: "GIF has 256 colours and no animation.",
    tiff: "TIFF files are uncompressed and can be large.",
    svg: "Your picture is embedded in the SVG; it is not converted to vector shapes."
  };
  function updateFormatDependentUI() {
    const f = formatSelect.value;
    const showQuality = QUALITY_FORMATS.includes(f) || f === "original";
    $("#qualityField").style.display = showQuality ? "block" : "none";
    $("#qualityHint").textContent = f === "original" ? " Applies to JPG, WEBP and AVIF. PNG is lossless." : "";
    const needsBg = !ALPHA_FORMATS.includes(f) && f !== "original" || !preserveAlpha.checked;
    $("#bgField").style.display = needsBg ? "block" : "none";
    $("#formatHint").textContent = FORMAT_HINTS[f] || "";
  }
  formatSelect.addEventListener("change", updateFormatDependentUI);
  preserveAlpha.addEventListener("change", updateFormatDependentUI);
  qualitySlider.addEventListener("input", () => qualityVal.textContent = qualitySlider.value);
  $$(".bgopt").forEach((o) => {
    o.addEventListener("click", () => {
      $$(".bgopt").forEach((x) => x.classList.remove("selected"));
      o.classList.add("selected");
    });
  });
  $("#customBg").addEventListener("input", () => {
    $$(".bgopt").forEach((x) => x.classList.remove("selected"));
    $(".bgopt.custom").classList.add("selected");
  });
  function currentBg() {
    const sel = document.querySelector(".bgopt.selected");
    if (!sel || sel.dataset.bg === "white") return "#ffffff";
    if (sel.dataset.bg === "black") return "#000000";
    return $("#customBg").value;
  }
  var aspect = 16 / 9;
  var dimsEdited = false;
  function showResizeBody() {
    $("#resizeBody").style.display = resizeToggle.checked || state.mode === "resize" ? "block" : "none";
  }
  resizeToggle.addEventListener("change", () => {
    showResizeBody();
    if (resizeToggle.checked) syncResizeInputs(false);
  });
  function syncResizeInputs(force) {
    if (unitSelect.value !== "px") return;
    const first = state.files[0];
    if (!first || !first.width) return;
    if (dimsEdited && !force) return;
    widthInput.value = first.width;
    heightInput.value = first.height;
    aspect = first.width / first.height;
    if (force) dimsEdited = false;
  }
  widthInput.addEventListener("input", () => {
    dimsEdited = true;
    if (!lockAspect.checked) return;
    const v = parseFloat(widthInput.value);
    heightInput.value = !(v >= 1) ? "" : unitSelect.value === "%" ? widthInput.value : Math.max(1, Math.round(v / aspect));
  });
  heightInput.addEventListener("input", () => {
    dimsEdited = true;
    if (!lockAspect.checked) return;
    const v = parseFloat(heightInput.value);
    widthInput.value = !(v >= 1) ? "" : unitSelect.value === "%" ? heightInput.value : Math.max(1, Math.round(v * aspect));
  });
  unitSelect.addEventListener("change", () => {
    if (unitSelect.value === "%") {
      widthInput.value = 100;
      heightInput.value = 100;
    } else if (state.files[0] && state.files[0].width) syncResizeInputs(true);
    else {
      widthInput.value = 1920;
      heightInput.value = 1080;
      aspect = 16 / 9;
    }
  });
  $$(".preset-chip").forEach((chip) => {
    chip.setAttribute("role", "button");
    chip.tabIndex = 0;
    const apply = () => {
      const w = +chip.dataset.w, h = +chip.dataset.h;
      if (w === 0) {
        if (state.mode === "resize") {
          unitSelect.value = "px";
          syncResizeInputs(true);
        } else {
          resizeToggle.checked = false;
          showResizeBody();
        }
        return;
      }
      resizeToggle.checked = true;
      showResizeBody();
      unitSelect.value = "px";
      widthInput.value = w;
      heightInput.value = h;
      aspect = w / h;
      dimsEdited = true;
    };
    chip.addEventListener("click", apply);
    chip.addEventListener("keydown", (e) => {
      if (e.key === "Enter" || e.key === " ") {
        e.preventDefault();
        apply();
      }
    });
  });
  $("#accToggle").setAttribute("role", "button");
  $("#accToggle").tabIndex = 0;
  $("#accToggle").setAttribute("aria-expanded", "false");
  function toggleAcc() {
    const open = $("#accBody").classList.toggle("open");
    $("#accChevron").classList.toggle("open", open);
    $("#accToggle").setAttribute("aria-expanded", String(open));
  }
  $("#accToggle").addEventListener("click", toggleAcc);
  $("#accToggle").addEventListener("keydown", (e) => {
    if (e.key === "Enter" || e.key === " ") {
      e.preventDefault();
      toggleAcc();
    }
  });
  [
    ["#metaSelect", "Browsers always remove photo metadata when re-encoding an image."],
    ["#progressiveJpg", "Not available when converting in the browser."],
    ["#chromaSelect", "Not available when converting in the browser."]
  ].forEach(([sel, why]) => {
    const c = $(sel);
    c.disabled = true;
    c.title = why;
    const row = c.closest(".acc-field");
    if (row) {
      row.classList.add("disabled");
      row.title = why;
    }
  });
  function applyMode(next) {
    if (state.mode && state.mode !== "about") savedSettings[state.mode] = { format: formatSelect.value, quality: qualitySlider.value };
    const changed = state.mode !== next;
    state.mode = next;
    document.body.dataset.mode = next;
    $$("#modeNav a").forEach((a) => {
      const on = a.dataset.mode === next;
      a.classList.toggle("active", on);
      if (on) a.setAttribute("aria-current", "page");
      else a.removeAttribute("aria-current");
    });
    const cfg = MODES[next];
    const isAbout = next === "about";
    $("#aboutSection").hidden = !isAbout;
    $("#heroSection").hidden = isAbout;
    document.title = isAbout ? "About \xB7 Image Converter" : `${cfg.title} \xB7 Image Converter`;
    if (isAbout) {
      window.scrollTo(0, 0);
      return;
    }
    $("#heroTitle").textContent = cfg.title;
    $("#heroLead").textContent = cfg.lead;
    $("#heroSub").textContent = cfg.sub;
    $("#settingsTitle").textContent = cfg.settings;
    const orig = formatSelect.querySelector('option[value="original"]');
    orig.hidden = orig.disabled = next === "convert";
    const s = savedSettings[next] || { format: cfg.format, quality: cfg.quality };
    formatSelect.value = s.format;
    if (formatSelect.value !== s.format) formatSelect.value = cfg.format;
    qualitySlider.value = s.quality;
    qualityVal.textContent = s.quality;
    const isResize = next === "resize";
    $("#resizeSwitchRow").style.display = isResize ? "none" : "flex";
    if (isResize) {
      resizeToggle.checked = true;
      syncResizeInputs(false);
    } else if (changed) resizeToggle.checked = false;
    showResizeBody();
    updateFormatDependentUI();
    if (changed) {
      state.results = [];
      $("#resultsPanel").style.display = "none";
      state.files.forEach((f) => {
        if (!f.unreadable) {
          f.status = "ready";
          f.error = "";
        }
      });
    }
    renderFileList();
    window.scrollTo(0, 0);
  }
  window.addEventListener("hashchange", () => {
    if (!state.converting) applyMode(modeFromHash());
    else location.hash = "#" + state.mode;
  });
  function buildName(base, ext, r, n) {
    const pattern = ($("#filenamePattern").value || "{name}").trim() || "{name}";
    let out = pattern.replaceAll("{name}", base).replaceAll("{format}", ext).replaceAll("{width}", r.width).replaceAll("{height}", r.height).replaceAll("{n}", n);
    out = out.replace(/[\\/:*?"<>|\u0000-\u001f]/g, "_").trim() || base;
    return `${out}.${ext}`;
  }
  var convertBtn = $("#convertBtn");
  convertBtn.addEventListener("click", runConversion);
  function readOpts() {
    return {
      mode: state.mode,
      format: formatSelect.value,
      quality: +qualitySlider.value,
      bg: currentBg(),
      resize: resizeToggle.checked || state.mode === "resize",
      width: parseFloat(widthInput.value),
      height: parseFloat(heightInput.value),
      unit: unitSelect.value,
      lock: lockAspect.checked,
      preserveAlpha: preserveAlpha.checked,
      dpi: parseFloat($("#dpiInput").value) || 72
    };
  }
  async function runConversion() {
    const items = queue();
    if (!items.length || state.converting) return;
    const cfg = MODES[state.mode];
    const opts = readOpts();
    if (opts.resize && !(opts.width >= 1 && opts.height >= 1)) {
      toast("Enter a width and height of at least 1.", "err");
      return;
    }
    state.converting = true;
    state.cancelRequested = false;
    convertBtn.disabled = true;
    $("#progressWrap").style.display = "block";
    $("#resultsPanel").style.display = "none";
    state.results = [];
    items.forEach((f) => {
      f.status = "ready";
      f.error = "";
    });
    renderFileList();
    const total = items.length;
    const usedNames = /* @__PURE__ */ new Set();
    let failed = 0;
    for (let i = 0; i < total; i++) {
      if (state.cancelRequested) break;
      const item = items[i];
      $("#progressText").textContent = `${cfg.ing} ${i + 1} of ${total}: ${item.name}`;
      const pct = Math.round(i / total * 100);
      $("#progressFill").style.width = pct + "%";
      $("#progressPct").textContent = pct + "%";
      await new Promise((r) => setTimeout(r, 30));
      const res = await convertImage(item, opts);
      if (res.ok) {
        item.status = "converted";
        const base = item.name.replace(/\.[^.]+$/, "");
        let name = buildName(base, res.ext, res, i + 1);
        for (let n = 1; usedNames.has(name.toLowerCase()); n++) name = buildName(base, res.ext, res, i + 1).replace(/(\.[^.]+)$/, ` (${n})$1`);
        usedNames.add(name.toLowerCase());
        state.results.push({
          id: item.id,
          thumb: item.url,
          originalName: item.name,
          newName: name,
          originalSize: item.size,
          convertedSize: res.blob.size,
          format: res.format,
          width: res.width,
          height: res.height,
          blob: res.blob,
          note: res.note || ""
        });
      } else {
        failed++;
        item.status = "failed";
        item.error = res.error;
      }
      const done = Math.round((i + 1) / total * 100);
      $("#progressFill").style.width = done + "%";
      $("#progressPct").textContent = done + "%";
    }
    const cancelled = state.cancelRequested;
    state.converting = false;
    renderFileList();
    await new Promise((r) => setTimeout(r, 200));
    $("#progressWrap").style.display = "none";
    updateConvertButton();
    if (cancelled) toast(state.results.length ? `Stopped. ${state.results.length} finished before you cancelled.` : "Cancelled.");
    if (state.results.length) showResults(failed);
    else if (!cancelled) toast("Couldn't process these images. Try another file or choose a different output format.", "err");
  }
  $("#cancelBtn").addEventListener("click", () => {
    state.cancelRequested = true;
  });
  function showResults(failedCount) {
    const cfg = MODES[state.mode];
    const n = state.results.length;
    $("#resultsPanel").style.display = "block";
    $("#resultsTitle").textContent = cfg.done;
    $("#resultsSubtext").textContent = `${n} image${n === 1 ? "" : "s"} ${cfg.doneNoun} successfully` + (failedCount ? `, ${failedCount} failed` : "");
    const totalOrig = state.results.reduce((a, r) => a + r.originalSize, 0);
    const totalNew = state.results.reduce((a, r) => a + r.convertedSize, 0);
    const savedPct = totalOrig > 0 ? Math.round((1 - totalNew / totalOrig) * 100) : 0;
    $("#savedPill").textContent = savedPct > 0 ? `Saved ${savedPct}% space` : savedPct < 0 ? `${Math.abs(savedPct)}% larger` : "Same size";
    const list = $("#resultsList");
    list.innerHTML = "";
    state.results.forEach((r) => {
      const card = el("div", "resultcard");
      card.innerHTML = `
      <img class="thumb" src="${r.thumb}" alt="">
      <div class="rinfo">
        <div class="rname" title="${esc(r.newName)}">${esc(r.newName)}</div>
        <div class="rmeta">${fmtSize(r.originalSize)} \u2192 ${fmtSize(r.convertedSize)} \u2022 ${LABEL[r.format] || ""} \u2022 ${r.width} \xD7 ${r.height}</div>
        ${r.note ? `<div class="rnote">${esc(r.note)}</div>` : ""}
      </div>
      <button class="btn btn-secondary btn-sm dl-one" aria-label="Download ${esc(r.newName)}">Download</button>`;
      card.querySelector(".dl-one").addEventListener("click", () => downloadResult(r));
      list.appendChild(card);
    });
    $("#resultsPanel").scrollIntoView({ behavior: "smooth", block: "nearest" });
    toast(`${n} image${n === 1 ? "" : "s"} ${cfg.doneNoun}.`);
  }
  function saveBlob(blob, filename) {
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = filename;
    a.rel = "noopener";
    document.body.appendChild(a);
    a.click();
    a.remove();
    setTimeout(() => URL.revokeObjectURL(url), 1500);
  }
  function downloadResult(r) {
    saveBlob(r.blob, r.newName);
  }
  $("#downloadAllBtn").addEventListener("click", () => {
    state.results.forEach((r, i) => setTimeout(() => downloadResult(r), i * 250));
    if (state.results.length > 1) toast("If your browser asks, allow multiple downloads. A ZIP is a single file.");
  });
  $("#downloadZipBtn").addEventListener("click", async () => {
    if (!state.results.length) return;
    try {
      const zip = await makeZip(state.results.map((r) => ({ name: r.newName, blob: r.blob })));
      saveBlob(zip, `${state.mode === "convert" ? "converted" : MODES[state.mode].doneNoun}-images.zip`);
    } catch (e) {
      toast("Couldn't create the ZIP. Try Download all instead.", "err");
    }
  });
  $("#newConversionBtn").addEventListener("click", () => {
    state.files.forEach((f) => URL.revokeObjectURL(f.url));
    state.files = [];
    state.results = [];
    dimsEdited = false;
    $("#resultsPanel").style.display = "none";
    renderFileList();
    window.scrollTo({ top: 0, behavior: "smooth" });
  });
  applyMode(modeFromHash());
})();

</script>
</body>
</html>
