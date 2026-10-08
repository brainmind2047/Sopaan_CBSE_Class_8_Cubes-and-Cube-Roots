<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Cubes and Cube Roots</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Class 8 Mathematics · Chapter 4</div>
  <div class="chapter-title">Cubes and Cube Roots</div>
  <div class="chapter-sub">Theory Notes · Practice by Learning Objective · Learning Assessment</div><div class="chapter-credit">Mixed multiple-choice and fill-in-the-blank practice · Chapter 4</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Class 8 Mathematics · Chapter 4<br>Chapter follows the Class 8 mathematics syllabus (New Enjoying Mathematics, Class 8). Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^y=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every part of the chapter, with the properties of cubes and cube roots and the book’s worked examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n41\">4.1 notes</button><button class=\"hub-btn\" data-jump=\"n42\">4.2 notes</button><button class=\"hub-btn\" data-jump=\"n43\">4.3 notes</button><button class=\"hub-btn\" data-jump=\"n44\">4.4 notes</button><button class=\"hub-btn\" data-jump=\"n45\">4.5 notes</button><button class=\"hub-btn\" data-jump=\"n46\">4.6 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by learning objective</h3><p>Every Example, Try This and Exercise question from the chapter, sorted by objective, mixing multiple-choice and fill-in-the-blank questions.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">4.1 · Cubes and perfect cubes</button><button class=\"hub-btn\" data-go=\"s2\">4.2 · Properties and patterns of cubes</button><button class=\"hub-btn\" data-go=\"s3\">4.3 · Prime factorisation of perfect cubes</button><button class=\"hub-btn\" data-go=\"s4\">4.4 · Making a number a perfect cube</button><button class=\"hub-btn\" data-go=\"s5\">4.5 · Cube roots by prime factorisation</button><button class=\"hub-btn\" data-go=\"s6\">4.6 · Cube roots by estimation</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments built from the Chapter Check-up. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s7\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s8\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s9\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s10\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>When a number is multiplied by itself three times we get its <b>cube</b>: 5<sup>3</sup> = 5 × 5 × 5 = 125. Going backwards, 5 is the <b>cube root</b> of 125, written ∛125 = 5. Cubes measure volume: a cube with edges of 1 cm has a volume of 1 cm × 1 cm × 1 cm = 1 cm<sup>3</sup> (one cubic centimetre).</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Finding cubes and cube roots, recognising perfect cubes.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Sums of cubes, odd-number patterns, making perfect cubes.</td></tr><tr><td>C</td><td>Communicating</td><td>Explaining rules, spotting mistakes and reasoning with digits.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Stacks of oranges, cube-shaped boxes and tanks, number puzzles.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top shows the time since you signed in. ✏️ opens a scratchpad with four pens for rough work. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> type negative numbers with the − key, e.g. <span class=\"mono\">-64</span>; fractions as <span class=\"mono\">-27/64</span> in lowest terms; decimals as <span class=\"mono\">0.064</span>. When a question asks for an exponent, type just the number.</p></section><section class=\"note\" id=\"n41\"><h2>4.1 Cubes and perfect cubes</h2><p class=\"lt\"><b>Objective:</b> Find the cube of integers, fractions and decimals, and recognise perfect (cubic) numbers.</p><p>x<sup>3</sup> = x × x × x is read “x cubed” or “x raised to the power 3”. So 1<sup>3</sup> = 1, 2<sup>3</sup> = 8, (−5)<sup>3</sup> = −125 and 30<sup>3</sup> = 30 × 30 × 30 = 27,000.</p><div class=\"fig\"><svg class=\"figsvg\" viewBox=\"0 0 155 198\" role=\"img\" style=\"max-width:155px\"><path class=\"sh\" d=\"M77.5,10.0 L100.1,23.0 L77.5,36.0 L55.0,23.0 Z\"/><path class=\"sh2\" d=\"M145.1,127.0 L122.6,140.0 L122.6,114.0 L145.1,101.0 Z\"/><path class=\"sh3\" d=\"M10.0,127.0 L32.5,140.0 L32.5,114.0 L10.0,101.0 Z\"/><path class=\"sh\" d=\"M55.0,23.0 L77.5,36.0 L55.0,49.0 L32.5,36.0 Z\"/><path class=\"sh2\" d=\"M145.1,101.0 L122.6,114.0 L122.6,88.0 L145.1,75.0 Z\"/><path class=\"sh3\" d=\"M10.0,101.0 L32.5,114.0 L32.5,88.0 L10.0,75.0 Z\"/><path class=\"sh\" d=\"M32.5,36.0 L55.0,49.0 L32.5,62.0 L10.0,49.0 Z\"/><path class=\"sh2\" d=\"M145.1,75.0 L122.6,88.0 L122.6,62.0 L145.1,49.0 Z\"/><path class=\"sh3\" d=\"M10.0,75.0 L32.5,88.0 L32.5,62.0 L10.0,49.0 Z\"/><path class=\"sh\" d=\"M100.1,23.0 L122.6,36.0 L100.1,49.0 L77.5,36.0 Z\"/><path class=\"sh2\" d=\"M122.6,140.0 L100.1,153.0 L100.1,127.0 L122.6,114.0 Z\"/><path class=\"sh3\" d=\"M32.5,140.0 L55.0,153.0 L55.0,127.0 L32.5,114.0 Z\"/><path class=\"sh\" d=\"M77.5,36.0 L100.1,49.0 L77.5,62.0 L55.0,49.0 Z\"/><path class=\"sh2\" d=\"M122.6,114.0 L100.1,127.0 L100.1,101.0 L122.6,88.0 Z\"/><path class=\"sh3\" d=\"M32.5,114.0 L55.0,127.0 L55.0,101.0 L32.5,88.0 Z\"/><path class=\"sh\" d=\"M55.0,49.0 L77.5,62.0 L55.0,75.0 L32.5,62.0 Z\"/><path class=\"sh2\" d=\"M122.6,88.0 L100.1,101.0 L100.1,75.0 L122.6,62.0 Z\"/><path class=\"sh3\" d=\"M32.5,88.0 L55.0,101.0 L55.0,75.0 L32.5,62.0 Z\"/><path class=\"sh\" d=\"M122.6,36.0 L145.1,49.0 L122.6,62.0 L100.1,49.0 Z\"/><path class=\"sh2\" d=\"M100.1,153.0 L77.5,166.0 L77.5,140.0 L100.1,127.0 Z\"/><path class=\"sh3\" d=\"M55.0,153.0 L77.5,166.0 L77.5,140.0 L55.0,127.0 Z\"/><path class=\"sh\" d=\"M100.1,49.0 L122.6,62.0 L100.1,75.0 L77.5,62.0 Z\"/><path class=\"sh2\" d=\"M100.1,127.0 L77.5,140.0 L77.5,114.0 L100.1,101.0 Z\"/><path class=\"sh3\" d=\"M55.0,127.0 L77.5,140.0 L77.5,114.0 L55.0,101.0 Z\"/><path class=\"sh\" d=\"M77.5,62.0 L100.1,75.0 L77.5,88.0 L55.0,75.0 Z\"/><path class=\"sh2\" d=\"M100.1,101.0 L77.5,114.0 L77.5,88.0 L100.1,75.0 Z\"/><path class=\"sh3\" d=\"M55.0,101.0 L77.5,114.0 L77.5,88.0 L55.0,75.0 Z\"/><text class=\"lb\" x=\"77.5\" y=\"188.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 × 3 × 3 = 3<tspan baseline-shift=\"super\" font-size=\"9\">3</tspan> = 27 unit cubes</text></svg></div><p>A cube with 3 unit cubes along each edge is made of 3 × 3 × 3 = 27 unit cubes, so its volume is 27 cm<sup>3</sup> when each small cube has edge 1 cm. This is why 27 is called a <b>cube number</b>.</p><p><b>Cube of a rational number:</b> ({a/b})<sup>3</sup> = a<sup>3</sup>/b<sup>3</sup>, so cube the numerator and the denominator separately. <b>Sign:</b> the cube of a positive number is positive and the cube of a negative number is negative.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 1)</div><div class=\"exl\">7<sup>3</sup> = 7 × 7 × 7 = <b>343</b>;  (−4)<sup>3</sup> = (−4) × (−4) × (−4) = <b>−64</b>.<br>({2/3})<sup>3</sup> = (2 × 2 × 2)/(3 × 3 × 3) = <b>{8/27}</b>;  (0.4)<sup>3</sup> = 0.4 × 0.4 × 0.4 = <b>0.064</b>;  ({−3/4})<sup>3</sup> = <b>{−27/64}</b>.</div></div><h4>Perfect cubes</h4><p>A <b>perfect cube</b> (cubic number) is a number obtained by multiplying a number by itself three times. 8, 27, 125, 343 and 512 are perfect cubes; 30, 65, 121 and 625 are not.</p><p>Cubes of the numbers 1 to 20:</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>n</th><th>n<sup>3</sup></th><th>n</th><th>n<sup>3</sup></th><th>n</th><th>n<sup>3</sup></th><th>n</th><th>n<sup>3</sup></th></tr><tr><td>1</td><td>1</td><td>6</td><td>216</td><td>11</td><td>1,331</td><td>16</td><td>4,096</td></tr><tr><td>2</td><td>8</td><td>7</td><td>343</td><td>12</td><td>1,728</td><td>17</td><td>4,913</td></tr><tr><td>3</td><td>27</td><td>8</td><td>512</td><td>13</td><td>2,197</td><td>18</td><td>5,832</td></tr><tr><td>4</td><td>64</td><td>9</td><td>729</td><td>14</td><td>2,744</td><td>19</td><td>6,859</td></tr><tr><td>5</td><td>125</td><td>10</td><td>1,000</td><td>15</td><td>3,375</td><td>20</td><td>8,000</td></tr></table></div><div class=\"keybox\"><b>Common mistake:</b> 30<sup>3</sup> means 30 × 30 × 30 = 27,000, not 30 + 30 + 30 = 90 and not 30 × 3 = 90.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 4.1 →</button></div></section><section class=\"note\" id=\"n42\"><h2>4.2 Properties and patterns of cubes</h2><p class=\"lt\"><b>Objective:</b> Use the units-digit and number-of-digits properties of cubes and write a cube as a sum of consecutive odd numbers.</p><h4>Units digit of a cube</h4><ul><li>Units digit 0, 1, 4, 5, 6 or 9 → the cube has the <b>same</b> units digit (14<sup>3</sup> = 2744, 25<sup>3</sup> = 15,625).</li><li>Units digit 2 → cube ends in 8, and units digit 8 → cube ends in 2 (8 + 2 = 10).</li><li>Units digit 3 → cube ends in 7, and units digit 7 → cube ends in 3 (7 + 3 = 10).</li></ul><p>The cube of an even number is even and the cube of an odd number is odd.</p><h4>Number of digits</h4><p>1 and 8 are the only one-digit cubes; 27 and 64 the only two-digit cubes; 125, 216, 343, 512 and 729 the only three-digit cubes. Cubes of 10 to 21 have four digits, of 22 to 46 five digits and of 47 to 99 six digits. Cubes of 3-digit numbers have 7, 8 or 9 digits.</p><h4>Sums of consecutive odd numbers</h4><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Sum of odd numbers</th><th>Cube</th></tr><tr><td>1</td><td>1 = 1<sup>3</sup></td></tr><tr><td>3 + 5</td><td>8 = 2<sup>3</sup></td></tr><tr><td>7 + 9 + 11</td><td>27 = 3<sup>3</sup></td></tr><tr><td>13 + 15 + 17 + 19</td><td>64 = 4<sup>3</sup></td></tr><tr><td>21 + 23 + 25 + 27 + 29</td><td>125 = 5<sup>3</sup></td></tr></table></div><p><b>n<sup>3</sup> is the sum of n consecutive odd numbers starting from n(n − 1) + 1.</b></p><div class=\"ex\"><div class=\"exh\">Worked example (10<sup>3</sup>)</div><div class=\"exl\">n = 10: start from 10 × 9 + 1 = 91 and add 10 consecutive odd numbers:<br>91 + 93 + 95 + 97 + 99 + 101 + 103 + 105 + 107 + 109 = <b>1000 = 10<sup>3</sup></b>.</div></div><h4>Cubes, squares and triangular numbers</h4><p>1<sup>3</sup> + 2<sup>3</sup> = 9 = (1 + 2)<sup>2</sup>, 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> = 36 = (1 + 2 + 3)<sup>2</sup>, and in general <b>1<sup>3</sup> + 2<sup>3</sup> + … + n<sup>3</sup> = (1 + 2 + … + n)<sup>2</sup> = [n(n + 1) ÷ 2]<sup>2</sup></b>.</p><div class=\"keybox\"><b>Quick check:</b> to find the units digit of a big cube such as 387<sup>3</sup>, cube only the units digit: 7<sup>3</sup> = 343, so 387<sup>3</sup> ends in 3.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 4.2 →</button></div></section><section class=\"note\" id=\"n43\"><h2>4.3 Prime factorisation of perfect cubes</h2><p class=\"lt\"><b>Objective:</b> Decide whether a number is a perfect cube by grouping its prime factors in triples.</p><p>In the cube of a number, every prime factor of the number appears three times: 10 = 2 × 5, so 10<sup>3</sup> = 2<sup>3</sup> × 5<sup>3</sup>. So <b>a number is a perfect cube if its prime factors can be grouped in triples of the same factor</b>, i.e. every exponent in its prime factorisation is a multiple of 3.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 2)</div><div class=\"exl\">10<sup>3</sup> = 10 × 10 × 10 = (2 × 2 × 2) × (5 × 5 × 5) = <b>2<sup>3</sup> × 5<sup>3</sup></b>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 3)</div><div class=\"exl\">432 = 3 × 3 × 3 × 2 × 2 × 2 × 2 = 3<sup>3</sup> × 2<sup>3</sup> × 2.<br>One factor 2 is left out of the triples, so <b>432 is not a perfect cube</b>.</div></div><div class=\"keybox\"><b>Method:</b> divide repeatedly by the smallest prime (short division), write the factors, then underline groups of three equal factors. Any factor left over means “not a perfect cube”.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 4.3 →</button></div></section><section class=\"note\" id=\"n44\"><h2>4.4 Making a number a perfect cube</h2><p class=\"lt\"><b>Objective:</b> Find the smallest number by which a number must be multiplied or divided to make it a perfect cube.</p><p>If some prime factors are not in complete triples, we can make a perfect cube in two ways:</p><ul><li><b>Multiply</b> by the factors that are missing to complete every triple.</li><li><b>Divide</b> by the factors that are left over.</li></ul><div class=\"ex\"><div class=\"exh\">Worked example (Example 5)</div><div class=\"exl\">576 = 2<sup>3</sup> × 2<sup>3</sup> × 3<sup>2</sup>: 3 appears only twice.<br>Multiply by one more 3: 576 × <b>3</b> = 1728 = 2<sup>3</sup> × 2<sup>3</sup> × 3<sup>3</sup> = 12<sup>3</sup>.</div></div><div class=\"ex\"><div class=\"exh\">Worked example (Example 7)</div><div class=\"exl\">10584 = 2<sup>3</sup> × 3<sup>3</sup> × 7 × 7: there are only two 7s.<br>Divide by 7 × 7 = <b>49</b>: 10584 ÷ 49 = 216 = 6<sup>3</sup>.</div></div><div class=\"keybox\"><b>Smallest multiplier:</b> for each prime, raise its exponent to the next multiple of 3. <b>Smallest divisor:</b> for each prime, remove the remainder when its exponent is divided by 3.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 4.4 →</button></div></section><section class=\"note\" id=\"n45\"><h2>4.5 Cube roots by prime factorisation</h2><p class=\"lt\"><b>Objective:</b> Find cube roots of integers, fractions and decimals (including negative numbers) by prime factorisation.</p><p>The <b>cube root</b> of a number is the number which, when cubed, gives the given number. 5<sup>3</sup> = 125, so ∛125 = 5. In general ∛(a<sup>3</sup>) = a.</p><p><b>Steps:</b> (1) write the number as a product of primes; (2) group equal primes in triples; (3) take one factor from each triple and multiply. E.g. 64 = (2 × 2 × 2) × (2 × 2 × 2), so ∛64 = 2 × 2 = 4.</p><ul><li>∛(a/b) = ∛a ÷ ∛b</li><li>∛(a × b) = ∛a × ∛b</li><li>∛(−a) = −∛a: the cube root of a negative number is negative.</li></ul><div class=\"ex\"><div class=\"exh\">Worked example (Example 9)</div><div class=\"exl\">1728 = (2 × 2 × 2) × (2 × 2 × 2) × (3 × 3 × 3), so ∛1728 = 2 × 2 × 3 = <b>12</b>.<br>∛(−74088) = −∛(2<sup>3</sup> × 3<sup>3</sup> × 7<sup>3</sup>) = −(2 × 3 × 7) = <b>−42</b>.<br>∛2.744 = ∛({2744/1000}) = ∛(2<sup>3</sup> × 7<sup>3</sup>) ÷ ∛(2<sup>3</sup> × 5<sup>3</sup>) = {14/10} = <b>1.4</b>.</div></div><div class=\"keybox\"><b>Decimals:</b> write the decimal as a fraction with denominator 1000, 1000000, … first. ∛0.008 = ∛({8/1000}) = {2/10} = 0.2.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 4.5 →</button></div></section><section class=\"note\" id=\"n46\"><h2>4.6 Cube roots by estimation</h2><p class=\"lt\"><b>Objective:</b> Find the cube root of a perfect cube from its units digit and groups of three digits, and state how many digits a cube root has.</p><p>For a number that is <b>known to be a perfect cube</b>, the cube root can be found from its digits.</p><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Units digit of the cube</th><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td></tr><tr><th>Units digit of the cube root</th><td>0</td><td>1</td><td>8</td><td>7</td><td>4</td><td>5</td><td>6</td><td>3</td><td>2</td><td>9</td></tr></table></div><p><b>Number of digits:</b> mark the digits in groups of three from the right; the number of groups is the number of digits in the cube root (50 653 → 2 groups → 2-digit root).</p><p><b>Steps:</b> (1) the first group (right-hand three digits) gives the units digit of the root from the table; (2) for the next group, find the largest cube not more than it: its cube root is the tens digit.</p><div class=\"ex\"><div class=\"exh\">Worked example (Example 10)</div><div class=\"exl\">4913 → groups 4 | 913. Units digit 3 → root ends in 7. Largest cube ≤ 4 is 1<sup>3</sup> → tens digit 1. ∛4913 = <b>17</b>.<br>238328 → 238 | 328. Units digit 8 → root ends in 2. Largest cube ≤ 238 is 216 = 6<sup>3</sup> → tens digit 6. ∛238328 = <b>62</b>.</div></div><div class=\"keybox\"><b>Negative numbers:</b> ∛(−175616) = −∛175616 = −56. This method only works if the number is a perfect cube.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 4.6 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>Find the cube of integers, fractions and decimals, and recognise perfect (cubic) numbers.</li><li>Use the units-digit and number-of-digits properties of cubes and write a cube as a sum of consecutive odd numbers.</li><li>Decide whether a number is a perfect cube by grouping its prime factors in triples.</li><li>Find the smallest number by which a number must be multiplied or divided to make it a perfect cube.</li><li>Find cube roots of integers, fractions and decimals (including negative numbers) by prime factorisation.</li><li>Find the cube root of a perfect cube from its units digit and groups of three digits, and state how many digits a cube root has.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s7\">Assessment A</button><button class=\"hub-btn\" data-go=\"s8\">Assessment B</button><button class=\"hub-btn\" data-go=\"s9\">Assessment C</button><button class=\"hub-btn\" data-go=\"s10\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s7", "A", "Knowing and understanding"], ["s8", "B", "Investigating patterns"], ["s9", "C", "Communicating"], ["s10", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "4.1 Cubes", "sub": "Cubes of integers, fractions and decimals; perfect cubes", "slides": [{"kind": "mcq", "text": "<b>Looking Back · Q2</b> · If x is any number, then “x cubed” is written as", "opts": ["3x", "x<sup>3</sup>", "x<sup>2</sup>", "x + x + x"], "correct": 1, "tag": "", "sol": "x cubed means x × x × x, which is written x<sup>3</sup>. 3x and x + x + x mean three x’s added together; x<sup>2</sup> is x squared."}, {"kind": "blank", "p": "<b>Looking Back · Q3</b> · When 1 is multiplied three times by itself, we get", "tag": "", "marks": "", "flat": [{"t": "1 × 1 × 1 = __B1__", "a": {"B1": "1"}}], "sol": "1 × 1 × 1 = 1, so 1<sup>3</sup> = 1."}, {"kind": "blank", "p": "<b>Example 1(a–c)</b> · Find the value of the following cubes.", "tag": "", "marks": "", "flat": [{"t": "a) 7<sup>3</sup> = __B1__", "a": {"B1": "343"}}, {"t": "b) 15<sup>3</sup> = __B1__", "a": {"B1": "3375"}}, {"t": "c) (−4)<sup>3</sup> = __B1__", "a": {"B1": "-64"}}], "sol": "7 × 7 × 7 = 343.\n15 × 15 × 15 = 225 × 15 = 3375.\n(−4) × (−4) × (−4) = 16 × (−4) = −64."}, {"kind": "mcq", "text": "<b>Example 1(d)</b> · ({2/3})<sup>3</sup> =", "opts": ["{2/27}", "{6/9}", "{8/9}", "{8/27}"], "correct": 3, "tag": "", "sol": "(2 × 2 × 2)/(3 × 3 × 3) = {8/27}. ({6/9} multiplies by 3 instead of cubing; {8/9} and {2/27} cube only one part.)"}, {"kind": "blank", "p": "<b>Example 1(e–g)</b> · Find the value of the following cubes.", "tag": "", "marks": "", "flat": [{"t": "e) (0.4)<sup>3</sup> = __B1__", "a": {"B1": "0.064"}, "expr": "dec"}, {"t": "f) (1.2)<sup>3</sup> = __B1__", "a": {"B1": "1.728"}, "expr": "dec"}, {"t": "g) ({−3/4})<sup>3</sup> = __B1__", "a": {"B1": "-27/64"}, "expr": "fl"}], "sol": "0.4 × 0.4 × 0.4 = 0.064 (3 decimal places).\n1.2 × 1.2 × 1.2 = 1.44 × 1.2 = 1.728.\n(−3) × (−3) × (−3) = −27 and 4 × 4 × 4 = 64, so {−27/64}: a negative number cubed is negative."}, {"kind": "mcq", "text": "<b>Common Mistake</b> · 30<sup>3</sup> =", "opts": ["90", "27000", "900", "2700"], "correct": 1, "tag": "", "sol": "30<sup>3</sup> = 30 × 30 × 30 = 900 × 30 = 27,000. Writing 30 + 30 + 30 = 90 adds instead of multiplying; 2700 and 900 lose zeros."}, {"kind": "mcq", "text": "Which of these numbers is <b>not</b> a perfect cube?", "opts": ["343", "125", "512", "121"], "correct": 3, "tag": "", "sol": "125 = 5<sup>3</sup>, 343 = 7<sup>3</sup> and 512 = 8<sup>3</sup>. 121 = 11 × 11 is a square but not a cube (4<sup>3</sup> = 64 and 5<sup>3</sup> = 125)."}, {"kind": "blank", "p": "<b>Ex 4A · Q1(a–d)</b> · Find the value of:", "tag": "", "marks": "", "flat": [{"t": "a) 3<sup>3</sup> = __B1__", "a": {"B1": "27"}}, {"t": "b) 8<sup>3</sup> = __B1__", "a": {"B1": "512"}}, {"t": "c) (60)<sup>3</sup> = __B1__", "a": {"B1": "216000"}}, {"t": "d) (−9)<sup>3</sup> = __B1__", "a": {"B1": "-729"}}], "sol": "3 × 3 × 3 = 27.\n8 × 8 × 8 = 512.\n6<sup>3</sup> × 10<sup>3</sup> = 216 × 1000 = 216,000.\n(−9) × (−9) × (−9) = 81 × (−9) = −729."}, {"kind": "mcq", "text": "<b>Ex 4A · Q1(e)</b> · ({3/4})<sup>3</sup> =", "opts": ["{27/64}", "{27/12}", "{9/16}", "{9/64}"], "correct": 0, "tag": "", "sol": "3<sup>3</sup>/4<sup>3</sup> = {27/64}."}, {"kind": "blank", "p": "<b>Ex 4A · Q1(f–h)</b> · Find the value of:", "tag": "", "marks": "", "flat": [{"t": "f) ({−2/3})<sup>3</sup> = __B1__", "a": {"B1": "-8/27"}, "expr": "fl"}, {"t": "g) (3.2)<sup>3</sup> = __B1__", "a": {"B1": "32.768"}, "expr": "dec"}, {"t": "h) (−0.5)<sup>3</sup> = __B1__", "a": {"B1": "-0.125"}, "expr": "dec"}], "sol": "(−2)<sup>3</sup>/3<sup>3</sup> = {−8/27}.\n3.2 × 3.2 = 10.24; 10.24 × 3.2 = 32.768.\n(−0.5) × (−0.5) × (−0.5) = 0.25 × (−0.5) = −0.125."}, {"kind": "mcq", "text": "<b>Ex 4A · Q1(i)</b> · (−0.2)<sup>3</sup> =", "opts": ["0.008", "−0.008", "−0.08", "−0.6"], "correct": 1, "tag": "", "sol": "0.2 × 0.2 × 0.2 = 0.008 (2 × 2 × 2 = 8 with 3 decimal places), and the cube of a negative number is negative: −0.008."}, {"kind": "blank", "p": "<b>Ex 4A · Q1(j–l)</b> · Find the value of:", "tag": "", "marks": "", "flat": [{"t": "j) (−0.4)<sup>3</sup> = __B1__", "a": {"B1": "-0.064"}, "expr": "dec"}, {"t": "k) (−40)<sup>3</sup> = __B1__", "a": {"B1": "-64000"}}, {"t": "l) ({4/9})<sup>3</sup> = __B1__", "a": {"B1": "64/729"}, "expr": "fl"}], "sol": "0.4<sup>3</sup> = 0.064, negative: −0.064.\n(−4)<sup>3</sup> × 10<sup>3</sup> = −64 × 1000 = −64,000.\n4<sup>3</sup>/9<sup>3</sup> = {64/729}."}, {"kind": "mcq", "text": "<b>Ex 4A · Q2</b> · Looking at the numbers 10000, 1000000, 100 and 1000, which of them are perfect cubes?", "opts": ["1000 only", "10000 and 1000 only", "100, 1000 and 1000000", "1000000 and 1000 only"], "correct": 3, "tag": "", "sol": "A power of 10 is a perfect cube when its number of zeros is a multiple of 3: 1000 = 10<sup>3</sup> and 1000000 = 100<sup>3</sup>. 10000 (4 zeros) and 100 (2 zeros) are not cubes."}, {"kind": "blank", "p": "Write the perfect cubes from Ex 4A · Q2 as cubes.", "tag": "", "marks": "", "flat": [{"t": "1000000 = (__B1__)<sup>3</sup>", "a": {"B1": "100"}}, {"t": "1000 = (__B1__)<sup>3</sup>", "a": {"B1": "10"}}], "sol": "100 × 100 × 100 = 1,000,000.\n10 × 10 × 10 = 1000."}]}, {"id": "s2", "label": "4.2 Patterns", "sub": "Properties of cubes: units digits, number of digits and sums of odd numbers", "slides": [{"kind": "mcq", "text": "A number ends in 2. Its cube ends in", "opts": ["6", "4", "2", "8"], "correct": 3, "tag": "", "sol": "Only the units digit matters: 2<sup>3</sup> = 8, so the cube ends in 8 (e.g. 12<sup>3</sup> = 1728)."}, {"kind": "blank", "p": "<b>Try This (p. 56)</b> · Find the units digit of the cube for each of the following numbers.", "tag": "", "marks": "", "flat": [{"t": "a) 323 → __B1__", "a": {"B1": "7"}}, {"t": "b) 5268 → __B1__", "a": {"B1": "2"}}, {"t": "c) 6666 → __B1__", "a": {"B1": "6"}}, {"t": "d) 2457 → __B1__", "a": {"B1": "3"}}], "sol": "Units digit 3: 3<sup>3</sup> = 27, so the cube ends in 7.\nUnits digit 8: 8<sup>3</sup> = 512, so the cube ends in 2.\nUnits digit 6: 6<sup>3</sup> = 216, so the cube ends in 6.\nUnits digit 7: 7<sup>3</sup> = 343, so the cube ends in 3."}, {"kind": "mcq", "text": "How many digits does the cube of any whole number from 22 to 46 have?", "opts": ["6", "5", "7", "4"], "correct": 1, "tag": "", "sol": "21<sup>3</sup> = 9261 (4 digits), 22<sup>3</sup> = 10,648 and 46<sup>3</sup> = 97,336 (5 digits), 47<sup>3</sup> = 103,823 (6 digits). So cubes of 22 to 46 have 5 digits."}, {"kind": "blank", "p": "<b>Ex 4A · Q3(a–c)</b> · Write the units digits of the following cubes.", "tag": "", "marks": "", "flat": [{"t": "a) (387)<sup>3</sup> → __B1__", "a": {"B1": "3"}}, {"t": "b) (83)<sup>3</sup> → __B1__", "a": {"B1": "7"}}, {"t": "c) (−81)<sup>3</sup> → __B1__", "a": {"B1": "1"}}], "sol": "7<sup>3</sup> = 343 → 3.\n3<sup>3</sup> = 27 → 7.\n1<sup>3</sup> = 1 → 1 ((−81)<sup>3</sup> = −531,441; the digit is 1, the number is negative)."}, {"kind": "mcq", "text": "<b>Ex 4A · Q3(d)</b> · The units digit of (680)<sup>3</sup> is", "opts": ["0", "2", "6", "8"], "correct": 0, "tag": "", "sol": "A number ending in 0 has a cube ending in 0 (in fact in 000): 680<sup>3</sup> = 314,432,000."}, {"kind": "blank", "p": "<b>Ex 4A · Q3(e, f)</b> · Write the units digits of the following cubes.", "tag": "", "marks": "", "flat": [{"t": "e) (864)<sup>3</sup> → __B1__", "a": {"B1": "4"}}, {"t": "f) (55)<sup>3</sup> → __B1__", "a": {"B1": "5"}}], "sol": "4<sup>3</sup> = 64 → 4.\n5<sup>3</sup> = 125 → 5."}, {"kind": "mcq", "text": "To write 10<sup>3</sup> as the sum of 10 consecutive odd numbers, the first odd number is n(n − 1) + 1 =", "opts": ["91", "81", "101", "90"], "correct": 0, "tag": "", "sol": "n = 10: 10 × 9 + 1 = 91, and 91 + 93 + … + 109 = 1000."}, {"kind": "blank", "p": "<b>Ex 4A · Q4(a, c)</b> · Find the odd numbers to be added to get the following cubes.", "tag": "", "marks": "", "flat": [{"t": "a) 7<sup>3</sup> = __B1__ (type all the odd numbers, separated by commas)", "a": {"B1": "43, 45, 47, 49, 51, 53, 55"}, "expr": "list"}, {"t": "c) 4<sup>3</sup> = __B1__ (type all the odd numbers, separated by commas)", "a": {"B1": "13, 15, 17, 19"}, "expr": "list"}], "sol": "Start at 7 × 6 + 1 = 43 and add 7 odd numbers: 43 + 45 + 47 + 49 + 51 + 53 + 55 = 343.\nStart at 4 × 3 + 1 = 13 and add 4 odd numbers: 13 + 15 + 17 + 19 = 64."}, {"kind": "mcq", "text": "<b>Ex 4A · Q4(b)</b> · 12<sup>3</sup> is the sum of 12 consecutive odd numbers. They run", "opts": ["from 133 to 157", "from 121 to 143", "from 133 to 155", "from 131 to 153"], "correct": 2, "tag": "", "sol": "Start at 12 × 11 + 1 = 133; 12 odd numbers: 133, 135, …, 155 (133 + 2 × 11 = 155). Their sum is 12 × 144 = 1728 = 12<sup>3</sup>."}]}, {"id": "s3", "label": "4.3 Prime factors", "sub": "Prime factorisation of perfect cubes — grouping factors in triples", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q1</b> · Factorise into primes (type the exponents).", "tag": "", "marks": "", "flat": [{"t": "a) 27 = 3 to the power __B1__", "a": {"B1": "3"}}, {"t": "b) 1000 = 2<sup>m</sup> × 5<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "3", "B2": "3"}}, {"t": "c) 1331 = 11 to the power __B1__", "a": {"B1": "3"}}], "sol": "27 = 3 × 3 × 3 = 3<sup>3</sup>.\n1000 = 10 × 10 × 10 = 2 × 2 × 2 × 5 × 5 × 5 = 2<sup>3</sup> × 5<sup>3</sup>.\n1331 = 11 × 11 × 11 = 11<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Looking Back · Q4(a)</b> · 8 in power notation using prime factorisation is", "opts": ["2<sup>3</sup>", "3<sup>2</sup>", "2<sup>4</sup>", "4<sup>2</sup>"], "correct": 0, "tag": "", "sol": "8 = 2 × 2 × 2 = 2<sup>3</sup>. (3<sup>2</sup> = 9, 2<sup>4</sup> = 16 and 4<sup>2</sup> = 16.)"}, {"kind": "blank", "p": "<b>Looking Back · Q4(b–e)</b> · Write in power notation using prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "b) 125 = (__B1__)<sup>3</sup>", "a": {"B1": "5"}}, {"t": "c) 343 = (__B1__)<sup>3</sup>", "a": {"B1": "7"}}, {"t": "d) 1000 = (__B1__)<sup>3</sup> × (__B2__)<sup>3</sup> (smaller prime first)", "a": {"B1": "2", "B2": "5"}}, {"t": "e) 4913 = (__B1__)<sup>3</sup>", "a": {"B1": "17"}}], "sol": "125 = 5 × 5 × 5 = 5<sup>3</sup>.\n343 = 7 × 7 × 7 = 7<sup>3</sup>.\n1000 = 2<sup>3</sup> × 5<sup>3</sup>.\n4913 ÷ 17 = 289 = 17 × 17, so 4913 = 17<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Example 2</b> · The prime factorisation of 10<sup>3</sup> is", "opts": ["2<sup>3</sup> × 5", "2 × 5<sup>3</sup>", "10 × 10 × 10 = 2<sup>10</sup>", "2<sup>3</sup> × 5<sup>3</sup>"], "correct": 3, "tag": "", "sol": "10 = 2 × 5, so 10<sup>3</sup> = (2 × 5)<sup>3</sup> = 2 × 2 × 2 × 5 × 5 × 5 = 2<sup>3</sup> × 5<sup>3</sup>."}, {"kind": "blank", "p": "<b>Example 3</b> · Is 432 a perfect cube?", "tag": "", "marks": "", "flat": [{"t": "432 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "4", "B2": "3"}}, {"t": "Is 432 a perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}], "sol": "432 = 2 × 2 × 2 × 2 × 3 × 3 × 3 = 2<sup>4</sup> × 3<sup>3</sup>.\nThe 3s form a triple but one factor 2 is left out, so 432 is not a perfect cube."}, {"kind": "mcq", "text": "<b>Example 4</b> · Check whether the number 37044 is a perfect cube by factorisation.", "opts": ["No, because 37044 is an even number", "Yes, because 37044 = 42<sup>3</sup>", "Yes, because there are three 3s and three 7s", "No, because there are only two 2s"], "correct": 3, "tag": "", "sol": "37044 = 2 × 2 × 3 × 3 × 3 × 7 × 7 × 7. The 3s and 7s are in triples but the 2s are not (only two), so it is not a perfect cube. (42<sup>3</sup> = 74,088.)"}, {"kind": "blank", "p": "<b>Ex 4B · Q1(a)</b> · Is 23328 a perfect cube? Use prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "23328 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "5", "B2": "6"}}, {"t": "Perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}], "sol": "23328 = 2<sup>5</sup> × 3<sup>6</sup>.\n3<sup>6</sup> = (3<sup>2</sup>)<sup>3</sup> is fine, but 5 is not a multiple of 3 (2<sup>5</sup> = 2<sup>3</sup> × 2 × 2), so 23328 is not a perfect cube."}, {"kind": "mcq", "text": "<b>Ex 4B · Q1(b)</b> · Using prime factorisation, which statement about 10648 is correct?", "opts": ["It is a perfect cube: 10648 = 22<sup>3</sup>", "It is a perfect cube: 10648 = 11<sup>3</sup>", "It is not a perfect cube: 11 is left out", "It is not a perfect cube: 10648 is even"], "correct": 0, "tag": "", "sol": "10648 = 2 × 2 × 2 × 11 × 11 × 11 = 2<sup>3</sup> × 11<sup>3</sup>. Both primes are in triples, so 10648 = (2 × 11)<sup>3</sup> = 22<sup>3</sup>."}, {"kind": "blank", "p": "<b>Ex 4B · Q1(c)</b> · Is 52488 a perfect cube? Use prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "52488 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "3", "B2": "8"}}, {"t": "Perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}], "sol": "52488 = 2<sup>3</sup> × 3<sup>8</sup>.\n3<sup>8</sup> = 3<sup>6</sup> × 3<sup>2</sup>: two 3s are left over, so 52488 is not a perfect cube."}, {"kind": "mcq", "text": "<b>Ex 4B · Q1(d)</b> · Is 74088 a perfect cube?", "opts": ["Yes: 74088 = 2<sup>3</sup> × 3<sup>3</sup> × 7<sup>3</sup> = 36<sup>3</sup>", "No: 74088 = 2<sup>3</sup> × 3<sup>3</sup> × 7<sup>2</sup>", "Yes: 74088 = 2<sup>3</sup> × 3<sup>3</sup> × 7<sup>3</sup> = 42<sup>3</sup>", "No: 74088 = 2<sup>2</sup> × 3<sup>3</sup> × 7<sup>3</sup>"], "correct": 2, "tag": "", "sol": "74088 ÷ 8 = 9261 = 27 × 343, so 74088 = 2<sup>3</sup> × 3<sup>3</sup> × 7<sup>3</sup> = (2 × 3 × 7)<sup>3</sup> = 42<sup>3</sup>."}, {"kind": "blank", "p": "<b>Ex 4B · Q1(e)</b> · Is 36864 a perfect cube? Use prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "36864 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "12", "B2": "2"}}, {"t": "Perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}], "sol": "36864 = 4096 × 9 = 2<sup>12</sup> × 3<sup>2</sup>.\n2<sup>12</sup> = (2<sup>4</sup>)<sup>3</sup> is a cube, but there are only two 3s, so 36864 is not a perfect cube."}, {"kind": "blank", "p": "<b>Ex 4B · Q1(f)</b> · Is 15625 a perfect cube? Use prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "15625 = 5 to the power __B1__", "a": {"B1": "6"}}, {"t": "15625 = (__B1__)<sup>3</sup>", "a": {"B1": "25"}}], "sol": "15625 = 5 × 5 × 5 × 5 × 5 × 5 = 5<sup>6</sup>.\nTwo triples of 5: 15625 = (5 × 5)<sup>3</sup> = 25<sup>3</sup>, so it is a perfect cube."}, {"kind": "mcq", "text": "<b>Project</b> · Extract the last four digits of the landline number 27662744 and the last six digits of the mobile number 99989176540. Which of them is a perfect cube?", "opts": ["neither of them", "2744 only", "both 2744 and 176540", "176540 only"], "correct": 1, "tag": "", "sol": "2744 = 2<sup>3</sup> × 7<sup>3</sup> = 14<sup>3</sup>, a perfect cube. 176540 = 2<sup>2</sup> × 5 × 7 × 13 × 97 (it also ends in 0 but not in 000), so it is not a perfect cube."}]}, {"id": "s4", "label": "4.4 Make a cube", "sub": "Smallest number to multiply or divide by to make a perfect cube", "slides": [{"kind": "blank", "p": "<b>Example 5</b> · Find out if 576 is a perfect cube. If not, find the smallest number that must be multiplied to make it a perfect cube.", "tag": "", "marks": "", "flat": [{"t": "576 = 2<sup>m</sup> × 3<sup>n</sup>:  m = __B1__ ,  n = __B2__", "a": {"B1": "6", "B2": "2"}}, {"t": "Smallest multiplier = __B1__", "a": {"B1": "3"}}, {"t": "The perfect cube obtained = __B1__", "a": {"B1": "1728"}}], "sol": "576 = 2 × 2 × 2 × 2 × 2 × 2 × 3 × 3 = 2<sup>6</sup> × 3<sup>2</sup>.\n3 appears only twice, so 576 is not a perfect cube; multiply by one more 3.\n576 × 3 = 1728 = 2<sup>3</sup> × 2<sup>3</sup> × 3<sup>3</sup> = 12<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Example 6</b> · What is the smallest number that must be multiplied by 385875 to make it a perfect cube?", "opts": ["3", "5", "9", "7"], "correct": 0, "tag": "", "sol": "385875 = 5 × 5 × 5 × 7 × 7 × 7 × 3 × 3 = 5<sup>3</sup> × 7<sup>3</sup> × 3<sup>2</sup>. The 5s and 7s are in triples but there are only two 3s, so multiply by 3: 385875 × 3 = 3<sup>3</sup> × 5<sup>3</sup> × 7<sup>3</sup> = 105<sup>3</sup>."}, {"kind": "blank", "p": "<b>Example 7</b> · What is the smallest number that must divide 10584 to make it a perfect cube?", "tag": "", "marks": "", "flat": [{"t": "10584 = 2<sup>3</sup> × 3<sup>3</sup> × 7 to the power __B1__", "a": {"B1": "2"}}, {"t": "Smallest divisor = __B1__", "a": {"B1": "49"}}, {"t": "The perfect cube obtained = __B1__", "a": {"B1": "216"}}], "sol": "10584 = 2 × 2 × 2 × 3 × 3 × 3 × 7 × 7.\nOnly two 7s: remove them by dividing by 7 × 7 = 49.\n10584 ÷ 49 = 216 = 6<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Ex 4B · Q2(a)</b> · The smallest number that must be multiplied with 5400 to make it a perfect cube is", "opts": ["25", "2", "3", "5"], "correct": 3, "tag": "", "sol": "5400 = 2<sup>3</sup> × 3<sup>3</sup> × 5<sup>2</sup>. One more 5 completes the triple: 5400 × 5 = 27000 = 30<sup>3</sup>."}, {"kind": "blank", "p": "<b>Ex 4B · Q2(b, c)</b> · What is the smallest number that must be multiplied with each number to make it a perfect cube?", "tag": "", "marks": "", "flat": [{"t": "b) 24,696 → __B1__", "a": {"B1": "3"}}, {"t": "c) 4,08,375 → __B1__", "a": {"B1": "11"}}], "sol": "24696 = 2<sup>3</sup> × 3<sup>2</sup> × 7<sup>3</sup>: multiply by 3 (→ 74088 = 42<sup>3</sup>).\n408375 = 3<sup>3</sup> × 5<sup>3</sup> × 11<sup>2</sup>: multiply by 11 (→ 4492125 = 165<sup>3</sup>)."}, {"kind": "mcq", "text": "<b>Ex 4B · Q2(d)</b> · The smallest number that must be multiplied with 1,42,884 to make it a perfect cube is", "opts": ["14", "2", "7", "42"], "correct": 0, "tag": "", "sol": "142884 = 2<sup>2</sup> × 3<sup>6</sup> × 7<sup>2</sup>. One 2 and one 7 are missing, so multiply by 2 × 7 = 14 (→ 2<sup>3</sup> × 3<sup>6</sup> × 7<sup>3</sup> = 126<sup>3</sup>)."}, {"kind": "blank", "p": "<b>Ex 4B · Q3(a, b)</b> · What is the smallest number that must divide each number to make it a perfect cube?", "tag": "", "marks": "", "flat": [{"t": "a) 3,70,440 → __B1__", "a": {"B1": "5"}}, {"t": "b) 11,576,250 → __B1__", "a": {"B1": "10"}}], "sol": "370440 = 2<sup>3</sup> × 3<sup>3</sup> × 5 × 7<sup>3</sup>: divide by 5 (→ 74088 = 42<sup>3</sup>).\n11576250 = 2 × 3<sup>3</sup> × 5<sup>4</sup> × 7<sup>3</sup>: the 2 and one 5 are left over, divide by 2 × 5 = 10 (→ 1157625 = 105<sup>3</sup>)."}, {"kind": "mcq", "text": "<b>Ex 4B · Q3(c)</b> · The smallest number that must divide 20,12,472 to make it a perfect cube is", "opts": ["11", "49", "3", "7"], "correct": 3, "tag": "", "sol": "2012472 = 2<sup>3</sup> × 3<sup>3</sup> × 7 × 11<sup>3</sup>. The single 7 is left over: 2012472 ÷ 7 = 287496 = 66<sup>3</sup>."}, {"kind": "blank", "p": "<b>Ex 4B · Q3(d)</b> · What is the smallest number that must divide 1,22,472 to make it a perfect cube?", "tag": "", "marks": "", "flat": [{"t": "Smallest divisor = __B1__", "a": {"B1": "21"}}, {"t": "Cube root of the perfect cube obtained = __B1__", "a": {"B1": "18"}}], "sol": "122472 = 2<sup>3</sup> × 3<sup>7</sup> × 7: one 3 and the 7 are left over, divide by 3 × 7 = 21.\n122472 ÷ 21 = 5832 = 2<sup>3</sup> × 3<sup>6</sup> = 18<sup>3</sup>."}, {"kind": "mcq", "text": "A number is 2<sup>4</sup> × 5<sup>3</sup> = 2000. By what smallest number must it be divided to make it a perfect cube?", "opts": ["5", "4", "2", "8"], "correct": 2, "tag": "", "sol": "The 5s form a triple; of the four 2s, one is left over. 2000 ÷ 2 = 1000 = 10<sup>3</sup>."}]}, {"id": "s5", "label": "4.5 Cube roots", "sub": "Cube roots by prime factorisation (integers, fractions, decimals, negatives)", "slides": [{"kind": "blank", "p": "<b>Looking Back · Q5</b> · The area of a town in the form of a square is 961 sq. km. What is the length of each side?", "tag": "", "marks": "", "flat": [{"t": "Side = __B1__ km", "a": {"B1": "31"}}], "sol": "Side × side = 961 and 31 × 31 = 961, so each side is √961 = 31 km. (This is a square root; in this chapter we find cube roots in the same way.)"}, {"kind": "mcq", "text": "Which statement is correct?", "opts": ["∛125 = {125/3}, because the root divides by 3", "∛125 = 5, because 5 × 5 × 5 = 125", "∛125 = 15, because 15 + 15 + 15 = 45", "∛125 = 25, because 25 × 5 = 125"], "correct": 1, "tag": "", "sol": "The cube root of a number is the number which, when cubed, gives the number: 5<sup>3</sup> = 125, so ∛125 = 5."}, {"kind": "blank", "p": "<b>Example 8(a–c)</b> · Find the cube roots of the given cubes.", "tag": "", "marks": "", "flat": [{"t": "a) ∛(8<sup>3</sup>) = __B1__", "a": {"B1": "8"}}, {"t": "b) ∛[({2/3})<sup>3</sup>] = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "c) ∛[({−5/7})<sup>3</sup>] = __B1__", "a": {"B1": "-5/7"}, "expr": "fl"}], "sol": "The cube root undoes the cube: ∛(8<sup>3</sup>) = 8.\n∛[({2/3})<sup>3</sup>] = {2/3}.\n∛[({−5/7})<sup>3</sup>] = {−5/7}."}, {"kind": "mcq", "text": "<b>Example 8(d)</b> · ∛(a<sup>3</sup>) =", "opts": ["a<sup>9</sup>", "3a", "a<sup>3</sup>", "a"], "correct": 3, "tag": "", "sol": "a × a × a = a<sup>3</sup>, so the cube root of a<sup>3</sup> is a."}, {"kind": "blank", "p": "<b>Example 8(e)</b> · Find the cube root.", "tag": "", "marks": "", "flat": [{"t": "∛[(3.8)<sup>3</sup>] = __B1__", "a": {"B1": "3.8"}, "expr": "dec"}], "sol": "∛[(3.8)<sup>3</sup>] = 3.8."}, {"kind": "blank", "p": "<b>Example 9(a, b)</b> · Find the cube root of:", "tag": "", "marks": "", "flat": [{"t": "a) ∛1728 = __B1__", "a": {"B1": "12"}}, {"t": "b) ∛(−74088) = __B1__", "a": {"B1": "-42"}}], "sol": "1728 = 2<sup>3</sup> × 2<sup>3</sup> × 3<sup>3</sup>, so ∛1728 = 2 × 2 × 3 = 12.\n∛(−74088) = −∛74088 = −∛(2<sup>3</sup> × 3<sup>3</sup> × 7<sup>3</sup>) = −(2 × 3 × 7) = −42."}, {"kind": "mcq", "text": "<b>Example 9(c)</b> · ∛({−64/125}) =", "opts": ["{4/5}", "{−4/25}", "{−4/5}", "{−8/25}"], "correct": 2, "tag": "", "sol": "−64 = (−4)<sup>3</sup> and 125 = 5<sup>3</sup>, so ∛({−64/125}) = ∛(−64)/∛125 = {−4/5}."}, {"kind": "blank", "p": "<b>Example 9(d, e)</b> · Find the cube root of:", "tag": "", "marks": "", "flat": [{"t": "d) ∛2.744 = __B1__", "a": {"B1": "1.4"}, "expr": "dec"}, {"t": "e) ∛(216 × 125) = __B1__", "a": {"B1": "30"}}], "sol": "2.744 = {2744/1000} = (2<sup>3</sup> × 7<sup>3</sup>)/(2<sup>3</sup> × 5<sup>3</sup>), so the cube root is {14/10} = 1.4.\n∛(216 × 125) = ∛216 × ∛125 = 6 × 5 = 30."}, {"kind": "blank", "p": "<b>Ex 4C · Q1(a–d)</b> · Find the cube roots of the following.", "tag": "", "marks": "", "flat": [{"t": "a) ∛(9<sup>3</sup>) = __B1__", "a": {"B1": "9"}}, {"t": "b) ∛[(−6)<sup>3</sup>] = __B1__", "a": {"B1": "-6"}}, {"t": "c) ∛[({−1/7})<sup>3</sup>] = __B1__", "a": {"B1": "-1/7"}, "expr": "fl"}, {"t": "d) ∛[({2/9})<sup>3</sup>] = __B1__", "a": {"B1": "2/9"}, "expr": "fl"}], "sol": "∛(9<sup>3</sup>) = 9.\n∛[(−6)<sup>3</sup>] = −6.\n∛[({−1/7})<sup>3</sup>] = {−1/7}.\n∛[({2/9})<sup>3</sup>] = {2/9}."}, {"kind": "mcq", "text": "<b>Ex 4C · Q1(e)</b> · ∛[(0.4)<sup>3</sup>] =", "opts": ["0.064", "1.2", "0.04", "0.4"], "correct": 3, "tag": "", "sol": "The cube root undoes the cube: ∛[(0.4)<sup>3</sup>] = 0.4. (0.064 is the value of (0.4)<sup>3</sup> itself.)"}, {"kind": "blank", "p": "<b>Ex 4C · Q1(f–h)</b> · Find the cube roots of the following.", "tag": "", "marks": "", "flat": [{"t": "f) ∛[(3.7)<sup>3</sup>] = __B1__", "a": {"B1": "3.7"}, "expr": "dec"}, {"t": "g) ∛[(−8.1)<sup>3</sup>] = __B1__", "a": {"B1": "-8.1"}, "expr": "dec"}, {"t": "h) ∛[(−0.3)<sup>3</sup>] = __B1__", "a": {"B1": "-0.3"}, "expr": "dec"}], "sol": "3.7.\n−8.1.\n−0.3."}, {"kind": "mcq", "text": "<b>Ex 4C · Q2(a)</b> · By prime factorisation, ∛343 =", "opts": ["17", "49", "7", "9"], "correct": 2, "tag": "", "sol": "343 = 7 × 7 × 7, one triple, so ∛343 = 7."}, {"kind": "blank", "p": "<b>Ex 4C · Q2(b–d)</b> · Find the cube roots by prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "b) ∛3375 = __B1__", "a": {"B1": "15"}}, {"t": "c) ∛13824 = __B1__", "a": {"B1": "24"}}, {"t": "d) ∛4.096 = __B1__", "a": {"B1": "1.6"}, "expr": "dec"}], "sol": "3375 = 3<sup>3</sup> × 5<sup>3</sup>, so ∛3375 = 3 × 5 = 15.\n13824 = 2<sup>9</sup> × 3<sup>3</sup> = (2<sup>3</sup>)<sup>3</sup> × 3<sup>3</sup>, so ∛13824 = 8 × 3 = 24.\n4.096 = {4096/1000} = 2<sup>12</sup>/(2<sup>3</sup> × 5<sup>3</sup>), so the cube root is 2<sup>4</sup>/(2 × 5) = {16/10} = 1.6."}, {"kind": "mcq", "text": "<b>Ex 4C · Q2(e)</b> · ∛({1331/2744}) =", "opts": ["{11/14}", "{121/196}", "{13/14}", "{11/12}"], "correct": 0, "tag": "", "sol": "1331 = 11<sup>3</sup> and 2744 = 2<sup>3</sup> × 7<sup>3</sup> = 14<sup>3</sup>, so the cube root is {11/14}."}, {"kind": "blank", "p": "<b>Ex 4C · Q2(f–h)</b> · Find the cube roots by prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "f) ∛({−216/35937}) = __B1__", "a": {"B1": "-2/11"}, "expr": "fv"}, {"t": "g) ∛(−5832) = __B1__", "a": {"B1": "-18"}}, {"t": "h) ∛(−0.001) = __B1__", "a": {"B1": "-0.1"}, "expr": "dec"}], "sol": "216 = 6<sup>3</sup> and 35937 = 3<sup>3</sup> × 11<sup>3</sup> = 33<sup>3</sup>, so the cube root is {−6/33} = {−2/11}.\n5832 = 2<sup>3</sup> × 3<sup>6</sup>, so ∛5832 = 2 × 9 = 18 and ∛(−5832) = −18.\n−0.001 = {−1/1000}, so the cube root is {−1/10} = −0.1."}, {"kind": "mcq", "text": "<b>Check-up · Mental Maths (a)</b> · The cube root of {−125/729} is", "opts": ["{5/9}", "{−5/9}", "{−25/81}", "{−5/27}"], "correct": 1, "tag": "", "sol": "−125 = (−5)<sup>3</sup> and 729 = 9<sup>3</sup>, so the cube root is {−5/9}."}, {"kind": "blank", "p": "<b>Check-up · Mental Maths (b–e)</b> · Find the cube root of:", "tag": "", "marks": "", "flat": [{"t": "b) 343 → __B1__", "a": {"B1": "7"}}, {"t": "c) {−64/216} → __B1__", "a": {"B1": "-2/3"}, "expr": "fv"}, {"t": "d) (0.216)<sup>3</sup> → __B1__", "a": {"B1": "0.216"}, "expr": "dec"}, {"t": "e) 25<sup>3</sup> → __B1__", "a": {"B1": "25"}}], "sol": "7<sup>3</sup> = 343.\n∛(−64)/∛216 = {−4/6} = {−2/3}.\nThe cube root undoes the cube: 0.216.\nThe cube root undoes the cube: 25."}]}, {"id": "s6", "label": "4.6 Estimation", "sub": "Cube roots of perfect cubes from units digits and groups of three digits", "slides": [{"kind": "mcq", "text": "A perfect cube ends in 8. Its cube root ends in", "opts": ["8", "2", "6", "4"], "correct": 1, "tag": "", "sol": "2<sup>3</sup> = 8, and no other digit has a cube ending in 8 (Table 4.1), so the cube root ends in 2."}, {"kind": "blank", "p": "Use groups of three digits from the right.", "tag": "", "marks": "", "flat": [{"t": "50653 → number of groups = __B1__", "a": {"B1": "2"}}, {"t": "So ∛50653 has __B1__ digits", "a": {"B1": "2"}}], "sol": "50 | 653: two groups.\nTwo groups → a 2-digit cube root (in fact ∛50653 = 37)."}, {"kind": "blank", "p": "<b>Example 10(a)</b> · Find the cube root of 4913 by estimation.", "tag": "", "marks": "", "flat": [{"t": "Units digit of the cube root = __B1__", "a": {"B1": "7"}}, {"t": "Tens digit of the cube root = __B1__", "a": {"B1": "1"}}, {"t": "∛4913 = __B1__", "a": {"B1": "17"}}], "sol": "Groups 4 | 913. The cube ends in 3, so the cube root ends in 7.\nThe largest cube not more than 4 is 1 = 1<sup>3</sup>, so the tens digit is 1.\n∛4913 = 17 (check: 17<sup>3</sup> = 4913)."}, {"kind": "mcq", "text": "<b>Example 10(b)</b> · ∛238328 =", "opts": ["58", "62", "68", "52"], "correct": 1, "tag": "", "sol": "238 | 328: the cube ends in 8, so the root ends in 2. The largest cube not more than 238 is 216 = 6<sup>3</sup>, so the tens digit is 6: ∛238328 = 62."}, {"kind": "blank", "p": "<b>Example 10(c)</b> · Find the cube root by estimation.", "tag": "", "marks": "", "flat": [{"t": "∛(−175616) = __B1__", "a": {"B1": "-56"}}], "sol": "∛(−175616) = −∛175616. 175 | 616: ends in 6 → units digit 6; largest cube ≤ 175 is 125 = 5<sup>3</sup> → tens digit 5. So the answer is −56."}, {"kind": "mcq", "text": "<b>Example 10(d)</b> · ∛({12167/68921}) =", "opts": ["{33/41}", "{23/49}", "{27/41}", "{23/41}"], "correct": 3, "tag": "", "sol": "12167: ends in 7 → units 3; largest cube ≤ 12 is 8 = 2<sup>3</sup> → 23. 68921: ends in 1 → units 1; largest cube ≤ 68 is 64 = 4<sup>3</sup> → 41. So {23/41}."}, {"kind": "blank", "p": "<b>Ex 4C · Q3(a–d)</b> · Find the units digits of the cube roots of the following cubic numbers.", "tag": "", "marks": "", "flat": [{"t": "a) 17576 → __B1__", "a": {"B1": "6"}}, {"t": "b) 42875 → __B1__", "a": {"B1": "5"}}, {"t": "c) 343000 → __B1__", "a": {"B1": "0"}}, {"t": "d) 205379 → __B1__", "a": {"B1": "9"}}], "sol": "Ends in 6 → 6.\nEnds in 5 → 5.\nEnds in 0 → 0.\nEnds in 9 → 9."}, {"kind": "mcq", "text": "<b>Ex 4C · Q3(e)</b> · The units digit of the cube root of −32768 is", "opts": ["2", "4", "6", "8"], "correct": 0, "tag": "", "sol": "Ignore the sign: 32768 ends in 8, so its cube root ends in 2 (∛(−32768) = −32)."}, {"kind": "blank", "p": "<b>Ex 4C · Q3(f–h)</b> · Find the units digits of the cube roots of the following cubic numbers.", "tag": "", "marks": "", "flat": [{"t": "f) −103823 → __B1__", "a": {"B1": "7"}}, {"t": "g) 21952 → __B1__", "a": {"B1": "8"}}, {"t": "h) 2197 → __B1__", "a": {"B1": "3"}}], "sol": "Ends in 3 → 7.\nEnds in 2 → 8.\nEnds in 7 → 3."}, {"kind": "blank", "p": "<b>Ex 4C · Q4(a–d)</b> · Find the tens digit of the cube roots of the numbers in Question 3.", "tag": "", "marks": "", "flat": [{"t": "a) 17576 → __B1__", "a": {"B1": "2"}}, {"t": "b) 42875 → __B1__", "a": {"B1": "3"}}, {"t": "c) 343000 → __B1__", "a": {"B1": "7"}}, {"t": "d) 205379 → __B1__", "a": {"B1": "5"}}], "sol": "17 | 576: largest cube ≤ 17 is 8 = 2<sup>3</sup> → 2 (root 26).\n42 | 875: 27 = 3<sup>3</sup> → 3 (root 35).\n343 | 000: 343 = 7<sup>3</sup> → 7 (root 70).\n205 | 379: 125 = 5<sup>3</sup> → 5 (root 59)."}, {"kind": "mcq", "text": "<b>Ex 4C · Q4(e)</b> · The tens digit of the cube root of −32768 is", "opts": ["4", "2", "1", "3"], "correct": 3, "tag": "", "sol": "32 | 768: the largest cube not more than 32 is 27 = 3<sup>3</sup>, so the tens digit is 3 (∛(−32768) = −32)."}, {"kind": "blank", "p": "<b>Ex 4C · Q4(f–h)</b> · Find the tens digit of the cube roots of the numbers in Question 3.", "tag": "", "marks": "", "flat": [{"t": "f) −103823 → __B1__", "a": {"B1": "4"}}, {"t": "g) 21952 → __B1__", "a": {"B1": "2"}}, {"t": "h) 2197 → __B1__", "a": {"B1": "1"}}], "sol": "103 | 823: 64 = 4<sup>3</sup> → 4 (root −47).\n21 | 952: 8 = 2<sup>3</sup> → 2 (root 28).\n2 | 197: 1 = 1<sup>3</sup> → 1 (root 13)."}, {"kind": "mcq", "text": "<b>Ex 4C · Q5(a)</b> · Using estimation, ∛592704 =", "opts": ["74", "86", "94", "84"], "correct": 3, "tag": "", "sol": "592 | 704: ends in 4 → units digit 4. 8<sup>3</sup> = 512 ≤ 592 < 729 = 9<sup>3</sup> → tens digit 8. So 84."}, {"kind": "blank", "p": "<b>Ex 4C · Q5(b–e)</b> · Find the cube roots of the following perfect cubes using estimation.", "tag": "", "marks": "", "flat": [{"t": "b) 24389 → __B1__", "a": {"B1": "29"}}, {"t": "c) 438976 → __B1__", "a": {"B1": "76"}}, {"t": "d) −185193 → __B1__", "a": {"B1": "-57"}}, {"t": "e) 778688 → __B1__", "a": {"B1": "92"}}], "sol": "24 | 389: ends in 9 → 9; 8 = 2<sup>3</sup> ≤ 24 → 2. So 29.\n438 | 976: ends in 6 → 6; 343 = 7<sup>3</sup> ≤ 438 → 7. So 76.\n185 | 193: ends in 3 → 7; 125 = 5<sup>3</sup> ≤ 185 → 5. So −57.\n778 | 688: ends in 8 → 2; 729 = 9<sup>3</sup> ≤ 778 → 9. So 92."}, {"kind": "mcq", "text": "<b>Ex 4C · Q6(a)</b> · The number of digits in the cube root of 729 is", "opts": ["2", "1", "9", "3"], "correct": 1, "tag": "", "sol": "729 has one group of three digits, so its cube root has 1 digit (∛729 = 9)."}, {"kind": "blank", "p": "<b>Ex 4C · Q6(b–e)</b> · Write the number of digits in the cube root of the following cubes.", "tag": "", "marks": "", "flat": [{"t": "b) 166375 → __B1__", "a": {"B1": "2"}}, {"t": "c) 1860867 → __B1__", "a": {"B1": "3"}}, {"t": "d) 94818816 → __B1__", "a": {"B1": "3"}}, {"t": "e) 205379 → __B1__", "a": {"B1": "2"}}], "sol": "166 | 375: 2 groups → 2 digits (55).\n1 | 860 | 867: 3 groups → 3 digits (123).\n94 | 818 | 816: 3 groups → 3 digits (456).\n205 | 379: 2 groups → 2 digits (59)."}]}, {"id": "s7", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "<b>Check-up · MCQ 1</b> · The one’s digit of the cube of 13 is", "opts": ["9", "3", "6", "7"], "correct": 3, "tag": "", "sol": "3<sup>3</sup> = 27, so 13<sup>3</sup> ends in 7 (13<sup>3</sup> = 2197)."}, {"kind": "mcq", "text": "<b>Check-up · MCQ 2</b> · Which of the following numbers is a perfect cube?", "opts": ["243", "216", "392", "8640"], "correct": 1, "tag": "", "sol": "216 = 2<sup>3</sup> × 3<sup>3</sup> = 6<sup>3</sup>. 243 = 3<sup>5</sup>, 392 = 2<sup>3</sup> × 7<sup>2</sup> and 8640 = 2<sup>6</sup> × 3<sup>3</sup> × 5 are not cubes."}, {"kind": "blank", "p": "<b>Check-up · Q3</b> · Find the cube of each of the following.", "tag": "", "marks": "", "flat": [{"t": "a) 12 → __B1__", "a": {"B1": "1728"}}, {"t": "b) 24 → __B1__", "a": {"B1": "13824"}}, {"t": "c) −49 → __B1__", "a": {"B1": "-117649"}}], "sol": "12 × 12 × 12 = 1728.\n24 × 24 × 24 = 576 × 24 = 13,824.\n(−49)<sup>3</sup> = −(49 × 49 × 49) = −(2401 × 49) = −1,17,649."}, {"kind": "blank", "p": "<b>Check-up · Q4(a–c)</b> · Find the cube root of each of the following using prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "a) 15625 → __B1__", "a": {"B1": "25"}}, {"t": "b) 0.125 → __B1__", "a": {"B1": "0.5"}, "expr": "dec"}, {"t": "c) ({−27/343}) → __B1__", "a": {"B1": "-3/7"}, "expr": "fl"}], "sol": "15625 = 5<sup>6</sup> = (5<sup>2</sup>)<sup>3</sup>, so the cube root is 25.\n0.125 = {125/1000} = 5<sup>3</sup>/10<sup>3</sup>, so the cube root is {5/10} = 0.5.\n−27 = (−3)<sup>3</sup> and 343 = 7<sup>3</sup>, so the cube root is {−3/7}."}, {"kind": "mcq", "text": "<b>Check-up · Q4(d)</b> · Using prime factorisation, ∛13824 =", "opts": ["34", "26", "14", "24"], "correct": 3, "tag": "", "sol": "13824 = 2<sup>9</sup> × 3<sup>3</sup>: ∛13824 = 2<sup>3</sup> × 3 = 24."}, {"kind": "blank", "p": "<b>Check-up · Q4(e, f)</b> · Find the cube root of each of the following using prime factorisation.", "tag": "", "marks": "", "flat": [{"t": "e) 250047 → __B1__", "a": {"B1": "63"}}, {"t": "f) 0.008 → __B1__", "a": {"B1": "0.2"}, "expr": "dec"}], "sol": "250047 = 3<sup>6</sup> × 7<sup>3</sup>, so the cube root is 3<sup>2</sup> × 7 = 63.\n0.008 = {8/1000} = 2<sup>3</sup>/10<sup>3</sup>, so the cube root is 0.2."}, {"kind": "mcq", "text": "Which statement is true?", "opts": ["The cube of an odd number is always odd", "Every number ending in 8 is a perfect cube", "The cube of a negative number is positive", "The cube root of a negative number is not defined"], "correct": 0, "tag": "", "sol": "odd × odd × odd is odd. (−2)<sup>3</sup> = −8 is negative; 18 ends in 8 but is not a cube; ∛(−8) = −2 exists."}, {"kind": "blank", "p": "<b>Check-up · Q5</b> · Find the cube root of each of the following perfect cubes by estimation.", "tag": "", "marks": "", "flat": [{"t": "a) 17576 → __B1__", "a": {"B1": "26"}}, {"t": "b) 132651 → __B1__", "a": {"B1": "51"}}, {"t": "c) 830584 → __B1__", "a": {"B1": "94"}}, {"t": "d) 21952 → __B1__", "a": {"B1": "28"}}], "sol": "17 | 576: units 6; 8 ≤ 17 → 2. So 26.\n132 | 651: units 1; 125 ≤ 132 → 5. So 51.\n830 | 584: units 4; 729 ≤ 830 → 9. So 94.\n21 | 952: units 8 (from 2); 8 ≤ 21 → 2. So 28."}]}, {"id": "s8", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "<b>Check-up · Q6</b> · Use 1<sup>3</sup> + 2<sup>3</sup> + … + n<sup>3</sup> = [n(n + 1) ÷ 2]<sup>2</sup>. Find the sum of:", "tag": "", "marks": "", "flat": [{"t": "a) 10 consecutive cubes starting from 1 = __B1__", "a": {"B1": "3025"}}, {"t": "b) 25 consecutive cubes starting from 1 = __B1__", "a": {"B1": "105625"}}], "sol": "[10 × 11 ÷ 2]<sup>2</sup> = 55<sup>2</sup> = 3025.\n[25 × 26 ÷ 2]<sup>2</sup> = 325<sup>2</sup> = 1,05,625."}, {"kind": "mcq", "text": "1<sup>3</sup> + 2<sup>3</sup> = (1 + 2)<sup>2</sup> and 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> = (1 + 2 + 3)<sup>2</sup>. What is 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> + 4<sup>3</sup>?", "opts": ["30", "100", "64", "1000"], "correct": 1, "tag": "", "sol": "(1 + 2 + 3 + 4)<sup>2</sup> = 10<sup>2</sup> = 100. Check: 1 + 8 + 27 + 64 = 100."}, {"kind": "blank", "p": "<b>Check-up · Q7</b> · Check whether the following numbers are perfect cubes. If not, find the smallest number that should be multiplied by the given numbers to make them perfect cubes.", "tag": "", "marks": "", "flat": [{"t": "a) 3267: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "a) smallest multiplier = __B1__", "a": {"B1": "11"}}, {"t": "b) 385875: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "b) smallest multiplier = __B1__", "a": {"B1": "3"}}, {"t": "c) −35721: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "c) smallest multiplier = __B1__", "a": {"B1": "7"}}], "sol": "3267 = 3<sup>3</sup> × 11<sup>2</sup>: only two 11s, so it is not a perfect cube.\nMultiply by one more 11: 3267 × 11 = 35937 = 33<sup>3</sup>.\n385875 = 3<sup>2</sup> × 5<sup>3</sup> × 7<sup>3</sup>: only two 3s, so it is not a perfect cube.\nMultiply by 3: 385875 × 3 = 1157625 = 105<sup>3</sup>.\n−35721 = −(3<sup>6</sup> × 7<sup>2</sup>): only two 7s, so it is not a perfect cube.\nMultiply by 7: −35721 × 7 = −250047 = (−63)<sup>3</sup>."}, {"kind": "blank", "p": "<b>Check-up · Q8</b> · Check whether the following numbers are perfect cubes. If not, find the smallest number that should divide the given numbers to make them perfect cubes.", "tag": "", "marks": "", "flat": [{"t": "a) 6125: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "a) smallest divisor = __B1__", "a": {"B1": "49"}}, {"t": "b) 47916: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "b) smallest divisor = __B1__", "a": {"B1": "36"}}, {"t": "c) 10584: perfect cube? (yes/no) __B1__", "a": {"B1": "no"}, "expr": "words"}, {"t": "c) smallest divisor = __B1__", "a": {"B1": "49"}}], "sol": "6125 = 5<sup>3</sup> × 7<sup>2</sup>: only two 7s, so it is not a perfect cube.\nDivide by 7 × 7 = 49: 6125 ÷ 49 = 125 = 5<sup>3</sup>.\n47916 = 2<sup>2</sup> × 3<sup>2</sup> × 11<sup>3</sup>: the 2s and 3s are not in triples, so it is not a perfect cube.\nDivide by 2 × 2 × 3 × 3 = 36: 47916 ÷ 36 = 1331 = 11<sup>3</sup>.\n10584 = 2<sup>3</sup> × 3<sup>3</sup> × 7<sup>2</sup>: only two 7s, so it is not a perfect cube.\nDivide by 49: 10584 ÷ 49 = 216 = 6<sup>3</sup>."}, {"kind": "mcq", "text": "<b>Did You Know?</b> · 1729 = 12<sup>3</sup> + 1<sup>3</sup> = 10<sup>3</sup> + 9<sup>3</sup> is the smallest number that is a sum of two cubes in two different ways. Which of these numbers can also be written as a sum of two cubes in two different ways?", "opts": ["4096", "4104", "2197", "1728"], "correct": 1, "tag": "", "sol": "4104 = 16<sup>3</sup> + 2<sup>3</sup> = 4096 + 8 and 4104 = 15<sup>3</sup> + 9<sup>3</sup> = 3375 + 729. (Another such number is 13832 = 24<sup>3</sup> + 2<sup>3</sup> = 20<sup>3</sup> + 18<sup>3</sup>.)"}, {"kind": "blank", "p": "<b>Did You Know?</b> · Find two such numbers: complete each number written as a sum of two cubes in two different ways.", "tag": "", "marks": "", "flat": [{"t": "4104 = 16<sup>3</sup> + 2<sup>3</sup> = 15<sup>3</sup> + (__B1__)<sup>3</sup>", "a": {"B1": "9"}}, {"t": "13832 = 24<sup>3</sup> + 2<sup>3</sup> = 20<sup>3</sup> + (__B1__)<sup>3</sup>", "a": {"B1": "18"}}], "sol": "16<sup>3</sup> + 2<sup>3</sup> = 4096 + 8 = 4104. 4104 − 15<sup>3</sup> = 4104 − 3375 = 729 = 9<sup>3</sup>.\n24<sup>3</sup> + 2<sup>3</sup> = 13824 + 8 = 13832. 13832 − 20<sup>3</sup> = 13832 − 8000 = 5832 = 18<sup>3</sup>."}, {"kind": "blank", "p": "<b>Check-up · HOTS 1</b> · Evaluate ∛0.003375.", "tag": "", "marks": "", "flat": [{"t": "∛0.003375 = __B1__", "a": {"B1": "0.15"}, "expr": "dec"}], "sol": "0.003375 = {3375/1000000} = (3<sup>3</sup> × 5<sup>3</sup>)/(10<sup>6</sup>) = 15<sup>3</sup>/100<sup>3</sup>, so the cube root is {15/100} = 0.15."}, {"kind": "mcq", "text": "13 + 15 + 17 + 19 = 4<sup>3</sup>. Which sum of consecutive odd numbers equals 6<sup>3</sup>?", "opts": ["31 + 33 + 35 + 37 + 39 + 41 + 43", "29 + 31 + 33 + 35 + 37 + 39", "31 + 33 + 35 + 37 + 39 + 41", "21 + 23 + 25 + 27 + 29 + 31"], "correct": 2, "tag": "", "sol": "Start at 6 × 5 + 1 = 31 and add 6 odd numbers: 31 + … + 41 = 216 = 6<sup>3</sup>."}, {"kind": "blank", "p": "Using n<sup>3</sup> = sum of n consecutive odd numbers starting from n(n − 1) + 1, write 8<sup>3</sup> as a sum.", "tag": "", "marks": "", "flat": [{"t": "First odd number = __B1__", "a": {"B1": "57"}}, {"t": "Last odd number = __B1__", "a": {"B1": "71"}}], "sol": "8 × 7 + 1 = 57.\n8 odd numbers: 57, 59, …, 57 + 2 × 7 = 71. Check: 8 × 64 = 512 = 8<sup>3</sup>."}, {"kind": "blank", "p": "<b>Check-up · HOTS 2</b> · Three numbers are in the ratio 5 : 3 : 7. The sum of their cubes is 61875. Find the three numbers.", "tag": "", "marks": "", "flat": [{"t": "The numbers are 5k, 3k, 7k with k = __B1__", "a": {"B1": "5"}}, {"t": "The numbers are __B1__ , __B2__ , __B3__ (in the ratio order)", "a": {"B1": "25", "B2": "15", "B3": "35"}}], "sol": "125k<sup>3</sup> + 27k<sup>3</sup> + 343k<sup>3</sup> = 495k<sup>3</sup> = 61875, so k<sup>3</sup> = 125 and k = 5.\n5 × 5 = 25, 3 × 5 = 15, 7 × 5 = 35."}]}, {"id": "s9", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "<b>Journal</b> · 2<sup>3</sup> = 8, 4<sup>3</sup> = 64, 8<sup>3</sup> = 512. What is the relation between these cubes, and does it hold for 3, 6 and 12?", "opts": ["Each cube is 4 times the one before; yes, because the numbers go up by 2 each time", "Each cube is 8 times the one before; yes, because doubling a number multiplies its cube by 2<sup>3</sup> = 8", "Each cube is 8 times the one before; no, because 3, 6 and 12 are not powers of 2", "Each cube is 2 times the one before; yes, because each number is double the one before"], "correct": 1, "tag": "", "sol": "64 = 8 × 8 and 512 = 8 × 64. For 3, 6, 12: 27, 216, 1728, and 216 = 8 × 27, 1728 = 8 × 216. In general (2a)<sup>3</sup> = 8a<sup>3</sup>."}, {"kind": "blank", "p": "Riya writes ∛0.027 = 0.03. Check her answer.", "tag": "", "marks": "", "flat": [{"t": "0.03 × 0.03 × 0.03 = __B1__", "a": {"B1": "0.000027"}, "expr": "dec"}, {"t": "The correct value of ∛0.027 = __B1__", "a": {"B1": "0.3"}, "expr": "dec"}], "sol": "0.03 × 0.03 × 0.03 = 0.000027 (6 decimal places), not 0.027, so Riya is wrong.\n0.027 = {27/1000} = 3<sup>3</sup>/10<sup>3</sup>, so ∛0.027 = {3/10} = 0.3. (Check: 0.3 × 0.3 × 0.3 = 0.027.)"}, {"kind": "mcq", "text": "Ravi writes 30<sup>3</sup> = 30 + 30 + 30 = 90. Which reply is correct?", "opts": ["Wrong: the exponent 3 means multiply three 30s, 30 × 30 × 30 = 27,000", "Wrong: 30<sup>3</sup> = 3<sup>3</sup> × 10 = 270", "Correct: the exponent 3 means add three 30s, so 30<sup>3</sup> = 90", "Wrong: 30<sup>3</sup> means 30 × 3, which is also 90 but written differently"], "correct": 0, "tag": "", "sol": "x<sup>3</sup> = x × x × x, so 30<sup>3</sup> = 27,000."}, {"kind": "blank", "p": "Complete the statements.", "tag": "", "marks": "", "flat": [{"t": "A number is a perfect cube if its prime factors can be grouped in __B1__ of the same factor.", "a": {"B1": "triples"}, "expr": "words", "accept": ["triplets", "threes", "groups of three"]}, {"t": "The cube of an even number is __B1__.", "a": {"B1": "even"}, "expr": "words"}, {"t": "The cube root of a negative number is __B1__.", "a": {"B1": "negative"}, "expr": "words"}], "sol": "Each prime factor of a number appears three times in its cube.\neven × even × even is even.\n∛(−a) = −∛a, e.g. ∛(−8) = −2."}, {"kind": "mcq", "text": "Why is ∛(−8) = −2?", "opts": ["Because (−2) × (−2) × (−2) = −8", "Because −8 ÷ 3 is close to −2", "Because (−2) × (−2) = 4 and 4 × 2 = 8", "Because 2 × 2 × 2 = 8 and cube roots are always positive"], "correct": 0, "tag": "", "sol": "The cube root of −8 is the number whose cube is −8, and (−2)<sup>3</sup> = −8."}, {"kind": "blank", "p": "912673 is a perfect cube. Find its cube root from its digits.", "tag": "", "marks": "", "flat": [{"t": "Its cube root ends in __B1__", "a": {"B1": "7"}}, {"t": "Its cube root is __B1__", "a": {"B1": "97"}}], "sol": "912673 ends in 3, and only 7<sup>3</sup> = 343 ends in 3, so the root ends in 7.\n912 | 673: 729 = 9<sup>3</sup> ≤ 912 < 1000, so the tens digit is 9: the cube root is 97."}, {"kind": "mcq", "text": "Meena says “1000 has 4 digits, so its cube root must have 4 digits.” Which reply is correct?", "opts": ["Yes: a cube root always has as many digits as the cube", "No: the root has 3 digits because 1000 has three zeros", "No: 1 | 000 is two groups of three digits, so the root has 2 digits (∛1000 = 10)", "No: the root has 1 digit because 1000 starts with 1"], "correct": 2, "tag": "", "sol": "Group the digits in threes from the right: 1 | 000. Two groups give a 2-digit cube root, and indeed 10<sup>3</sup> = 1000."}]}, {"id": "s10", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "mcq", "text": "<b>Check-up · Case study Q9(a)</b> · Oranges are stacked in a box so that each stack has the same number of oranges in each row as the number of rows. There are 12 such stacks in the box, and the number of rows is the same as the number of stacks. What is the total number of oranges in the box?", "opts": ["1728", "288", "144", "36"], "correct": 0, "tag": "", "sol": "12 stacks × 12 rows × 12 oranges per row = 12<sup>3</sup> = 1728 oranges.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 294 268\" role=\"img\" style=\"max-width:300px\"><circle cx=\"60.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"16.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"36.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"55.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"75.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"94.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"114.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"133.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"153.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"172.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"192.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"211.5\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"60.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"80.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"99.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"119.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"138.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"158.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"177.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"197.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"216.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"236.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"255.5\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><circle cx=\"275.0\" cy=\"231.0\" r=\"8.5\" style=\"fill:var(--gold-soft);stroke:var(--gold);stroke-width:1.1\"/><text class=\"lb\" x=\"4\" y=\"16.5\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"font-size:11px\">row 1</text><text class=\"lb\" x=\"4\" y=\"36.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"font-size:11px\">row 2</text><text class=\"lb\" x=\"4\" y=\"231.0\" text-anchor=\"start\" dominant-baseline=\"middle\" style=\"font-size:11px\">last row</text><text class=\"lb\" x=\"173.0\" y=\"256.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">One stack (front view)</text></svg>"}, {"kind": "blank", "p": "<b>Check-up · Case study Q9(b)</b> · In the same box, how many oranges are there in each stack?", "tag": "", "marks": "", "flat": [{"t": "Oranges in each stack = __B1__", "a": {"B1": "144"}}], "sol": "Each stack has 12 rows of 12 oranges: 12 × 12 = 144."}, {"kind": "mcq", "text": "<b>Check-up · Everyday Maths Q10</b> · Ira thought of the number 6912. Her brother has to make it a perfect cube by multiplying it by the least possible number. What is that number?", "opts": ["6", "3", "2", "4"], "correct": 2, "tag": "", "sol": "6912 = 2<sup>8</sup> × 3<sup>3</sup>. 2<sup>8</sup> needs one more 2 to become 2<sup>9</sup>, so multiply by 2: 13824 = 24<sup>3</sup>."}, {"kind": "blank", "p": "Continuing Everyday Maths Q10: Ira’s brother multiplies 6912 by the least number.", "tag": "", "marks": "", "flat": [{"t": "The perfect cube he gets = __B1__", "a": {"B1": "13824"}}, {"t": "Its cube root = __B1__", "a": {"B1": "24"}}], "sol": "6912 × 2 = 13824.\n13824 = 2<sup>9</sup> × 3<sup>3</sup>, so its cube root is 2<sup>3</sup> × 3 = 24."}, {"kind": "mcq", "text": "A cube-shaped water tank holds 3375 cubic metres of water when full. What is the length of each edge?", "opts": ["25 m", "1125 m", "15 m", "58 m"], "correct": 2, "tag": "", "sol": "Volume = edge<sup>3</sup>, so edge = ∛3375 = ∛(3<sup>3</sup> × 5<sup>3</sup>) = 15 m."}, {"kind": "blank", "p": "A cube-shaped box has edges of 1.2 m.", "tag": "", "marks": "", "flat": [{"t": "Volume = __B1__ m<sup>3</sup>", "a": {"B1": "1.728"}, "expr": "dec"}], "sol": "1.2 × 1.2 × 1.2 = 1.728 m<sup>3</sup>."}, {"kind": "mcq", "text": "A large cube is built from 512 small cubes of edge 1 cm. How many small cubes lie along each edge?", "opts": ["8", "128", "64", "16"], "correct": 0, "tag": "", "sol": "512 = 2<sup>9</sup> = (2<sup>3</sup>)<sup>3</sup> = 8<sup>3</sup>, so 8 small cubes lie along each edge."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-c8-ch4';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Cubes and Cube Roots</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };

renderLogin();
})();
</script>
</body>
</html>
