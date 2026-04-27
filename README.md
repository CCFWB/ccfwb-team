<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="CCFWB Team">
<title>CCFWB Team v10</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --ocean-blue:#5279A0;
  --ocean-blue-dark:#3F6285;
  --tide:#62A8AB;
  --tide-dark:#4A8C8F;
  --tide-light:#DCEEEF;
  --sunrise:#F4BE51;
  --sunrise-light:#FCEBC0;
  --sunrise-dark:#8B6014;
  --sand:#EBE9DF;
  --sand-soft:#F5F3EB;
  --sand-deep:#DEDBCF;
  --bg:var(--sand);
  --surface:#fff;
  --s2:var(--sand-deep);
  --border:#C9C5B7;
  --text:#1A2632;
  --muted:#6E7782;
  --accent:var(--ocean-blue);
  --accent-dark:var(--ocean-blue-dark);
  --al:#E5EDF5;
  --warn:#C17B2A;--wl:#FDF3E3;
  --danger:#A33030;--dl:#FDEAEA;
  --evc:var(--tide-dark);--evb:var(--tide-light);
  --prc:#2C5282;--prb:#EBF2FB;
  --adc:var(--sunrise-dark);--adb:#FEF6E0;
  --voc:#6B2FA0;--vob:#F5EEFF;
  --anc:#2A5780;--anb:#E1EBF5;
  --kac:#7A3A1A;--kab:#FAF0E8;
  --agc:#E8603E;--agb:#FAE2D5;
  --r:14px;--rs:10px;
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;font-size:17px;line-height:1.55}
#settingsOverlay{position:fixed;top:0;left:0;right:0;bottom:0;background:#1F3550;z-index:9999;overflow-y:auto;padding:48px 20px 32px;display:none;flex-direction:column;gap:18px}
#settingsOverlay.open{display:flex}
.so-title{font-family:'DM Serif Display',serif;font-size:28px;color:white;margin-bottom:4px}
.so-sub{font-size:13px;color:rgba(255,255,255,0.55);margin-bottom:8px;text-transform:uppercase;letter-spacing:0.12em}
.so-card{background:rgba(255,255,255,0.1);border-radius:var(--r);padding:18px}
.so-label{font-size:12px;color:rgba(255,255,255,0.6);text-transform:uppercase;letter-spacing:0.1em;margin-bottom:9px;font-weight:600}
.so-value{font-size:14px;color:white;word-break:break-all;margin-bottom:11px;background:rgba(255,255,255,0.08);padding:10px 12px;border-radius:8px}
.so-input{width:100%;padding:12px 14px;border:none;border-radius:8px;font-family:'DM Sans',sans-serif;font-size:15px;color:var(--text);background:rgba(255,255,255,0.92);outline:none;margin-bottom:9px}
.so-btn{padding:11px 20px;border:none;border-radius:8px;font-family:'DM Sans',sans-serif;font-size:14px;font-weight:600;cursor:pointer}
.so-btn.green{background:var(--sunrise);color:var(--sunrise-dark)}
.so-btn.red{background:rgba(163,48,48,0.9);color:white}
.so-saved{font-size:13px;color:var(--sunrise);margin-left:10px;display:none;font-weight:600}
.so-close{width:100%;padding:14px;background:rgba(255,255,255,0.12);color:white;border:1px solid rgba(255,255,255,0.25);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:16px;font-weight:500;cursor:pointer;margin-top:8px}
.setup{position:fixed;inset:0;background:linear-gradient(155deg,var(--accent) 0%,var(--accent-dark) 100%);z-index:500;display:flex;flex-direction:column;justify-content:flex-start;padding:48px 24px 32px;overflow-y:auto}
.setup.gone{display:none}
.setup-logo{font-family:'DM Serif Display',serif;font-size:34px;color:white;margin-bottom:4px;line-height:1.1}
.setup-sub{font-size:12px;letter-spacing:0.12em;text-transform:uppercase;color:rgba(255,255,255,0.7);margin-bottom:28px}
.setup-card{background:white;border-radius:var(--r);padding:20px;margin-bottom:14px}
.setup-card h3{font-size:16px;font-weight:600;margin-bottom:9px;color:var(--text)}
.setup-card p{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:10px}
.si{width:100%;padding:12px 14px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:15px;color:var(--text);background:var(--bg);outline:none;margin-bottom:10px}
.si:focus{border-color:var(--accent);background:white}
.sb{width:100%;padding:14px;background:var(--accent);color:white;border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:16px;font-weight:600;cursor:pointer}
.sb:disabled{opacity:0.5}
.sbo{width:100%;padding:12px;background:transparent;color:rgba(255,255,255,0.85);border:1px solid rgba(255,255,255,0.35);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;cursor:pointer;margin-top:8px}
.serr{font-size:13px;color:var(--danger);background:var(--dl);padding:9px 11px;border-radius:8px;margin-top:8px;display:none}
.scopy{font-size:13px;color:var(--accent);background:var(--al);padding:9px 13px;border-radius:var(--rs);word-break:break-all;cursor:pointer;margin-top:8px;display:none}
.loader{position:fixed;inset:0;background:rgba(235,233,223,0.92);z-index:300;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;font-size:15px;color:var(--muted)}
.loader.gone{display:none}
.spin{width:30px;height:30px;border:2.5px solid var(--border);border-top-color:var(--accent);border-radius:50%;animation:spin 0.7s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.notif{position:fixed;top:12px;right:12px;z-index:8000;background:white;border:1px solid var(--border);border-radius:20px;padding:7px 15px 7px 11px;display:flex;align-items:center;gap:8px;font-size:13px;color:var(--accent);font-weight:600;box-shadow:0 2px 14px rgba(0,0,0,0.1);opacity:0;transform:translateY(-8px);transition:opacity 0.3s,transform 0.3s;pointer-events:none}
.notif.show{opacity:1;transform:translateY(0)}
.ndot{width:8px;height:8px;border-radius:50%;background:var(--accent);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
.hdr{background:linear-gradient(155deg,var(--accent) 0%,var(--accent-dark) 70%,var(--tide-dark) 100%);color:white;padding:50px 20px 18px;position:relative;overflow:hidden}
.hdr::before{content:'';position:absolute;top:-60px;right:-60px;width:220px;height:220px;border-radius:50%;background:radial-gradient(circle,var(--sunrise) 0%,transparent 70%);opacity:0.32;pointer-events:none}
.hdr-sub{font-size:12px;letter-spacing:0.14em;text-transform:uppercase;color:var(--sunrise-light);margin-bottom:4px;font-weight:500;position:relative}
.hdr h1{font-family:'DM Serif Display',serif;font-size:30px;font-weight:400;line-height:1.15;position:relative}
.hdr-row{display:flex;align-items:center;gap:8px;margin-top:12px;flex-wrap:wrap;position:relative}
.hdr-stat{font-size:13px;color:rgba(255,255,255,0.92);background:rgba(255,255,255,0.15);padding:5px 12px;border-radius:20px;font-weight:500}
.hdr-clock{font-size:14px;font-weight:600;font-variant-numeric:tabular-nums;background:rgba(255,255,255,0.15);border:1px solid rgba(255,255,255,0.25);padding:5px 12px;border-radius:20px;letter-spacing:0.02em;color:white;display:inline-flex;align-items:center;gap:6px}
.hdr-clock::before{content:'';width:6px;height:6px;border-radius:50%;background:var(--sunrise);box-shadow:0 0 8px var(--sunrise);animation:pulse 2s infinite}
.settings-btn{margin-left:auto;background:rgba(255,255,255,0.2);border:2px solid rgba(255,255,255,0.4);color:white;font-size:18px;width:42px;height:42px;border-radius:50%;cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0;-webkit-appearance:none;appearance:none}
.syncbar{background:white;border-bottom:1px solid var(--border);padding:7px 16px;display:flex;align-items:center;gap:9px;font-size:13px;color:var(--muted)}
.sdot{width:8px;height:8px;border-radius:50%;background:var(--border);flex-shrink:0;transition:background 0.3s}
.sdot.syncing{background:var(--sunrise);animation:blink 0.8s infinite}
.sdot.synced{background:var(--accent)}
.sdot.error{background:var(--danger)}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0.3}}
.slbl{flex:1}
.sact{background:none;border:none;color:var(--accent);font-size:13px;font-family:'DM Sans',sans-serif;cursor:pointer;padding:2px 6px;font-weight:600}
.tabs{background:white;border-bottom:1px solid var(--border);display:flex;overflow-x:auto;scrollbar-width:none;padding:0 8px;gap:2px}
.tabs::-webkit-scrollbar{display:none}
.tab{padding:12px 14px;font-size:14px;font-weight:600;color:var(--muted);border-bottom:2px solid transparent;white-space:nowrap;cursor:pointer;background:none;border-top:none;border-left:none;border-right:none;font-family:'DM Sans',sans-serif}
.tab.on{color:var(--accent);border-bottom-color:var(--accent)}
.tdiv{width:1px;background:var(--border);margin:8px 4px;flex-shrink:0}
.tc{display:inline-flex;align-items:center;justify-content:center;min-width:18px;height:18px;border-radius:9px;font-size:11px;font-weight:600;padding:0 5px;margin-left:6px;background:var(--s2);color:var(--muted);line-height:1}
.tab.on .tc{background:var(--al);color:var(--accent)}
.tc.w{background:var(--sunrise-light);color:var(--sunrise-dark)}
.tc.d{background:var(--dl);color:var(--danger)}
.tc.a{background:var(--prb);color:var(--prc)}
.main{padding:18px;max-width:620px;margin:0 auto}
.sg{display:grid;grid-template-columns:1fr 1fr 1fr;gap:11px;margin-bottom:22px}
.sc{background:white;border:1px solid var(--border);border-radius:var(--rs);padding:14px;text-align:center}
.sc .n{font-family:'DM Serif Display',serif;font-size:32px;line-height:1;margin-bottom:5px}
.sc .l{font-size:12px;color:var(--muted);letter-spacing:0.06em;text-transform:uppercase;font-weight:500}
.n-t{color:var(--muted)}.n-p{color:var(--warn)}.n-d{color:var(--accent)}
.focus-banner{background:linear-gradient(135deg,var(--sunrise-light) 0%,#FFF6DB 100%);border:1px solid #F0D69A;border-radius:var(--r);padding:16px 18px;margin-bottom:20px;box-shadow:0 1px 3px rgba(139,96,20,0.06)}
.focus-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:11px}
.focus-title{font-family:'DM Serif Display',serif;font-size:18px;font-weight:400;color:var(--sunrise-dark);display:flex;align-items:center;gap:7px}
.focus-sub{font-size:11px;color:#B07B3A;letter-spacing:0.08em;text-transform:uppercase;margin-top:2px;font-weight:500}
.focus-add-btn{background:rgba(255,255,255,0.75);border:1px solid #F0D69A;color:var(--sunrise-dark);font-size:13px;font-weight:600;padding:6px 14px;border-radius:20px;cursor:pointer;font-family:'DM Sans',sans-serif}
.focus-list{display:flex;flex-direction:column;gap:7px}
.focus-item{display:flex;align-items:flex-start;gap:11px;padding:9px 11px;background:rgba(255,255,255,0.65);border-radius:var(--rs)}
.focus-item.done{opacity:0.55}
.focus-item.done .focus-text{text-decoration:line-through}
.focus-chk{width:22px;height:22px;border-radius:5px;border:1.5px solid #B07B3A;background:white;cursor:pointer;flex-shrink:0;margin-top:1px;display:flex;align-items:center;justify-content:center;font-size:14px;color:var(--sunrise-dark)}
.focus-chk.on{background:var(--sunrise-dark);border-color:var(--sunrise-dark);color:white}
.focus-text{flex:1;font-size:14px;color:var(--text);line-height:1.4}
.focus-meta{font-size:11px;color:#B07B3A;margin-top:3px}
.focus-del{background:none;border:none;color:#B07B3A;font-size:18px;cursor:pointer;padding:0 4px;line-height:1;opacity:0.5}
.focus-empty{font-size:13px;color:#B07B3A;font-style:italic;padding:6px 10px}
.focus-form{background:rgba(255,255,255,0.75);border-radius:var(--rs);padding:11px;margin-top:9px;display:none}
.focus-form.open{display:block}
.focus-input{width:100%;padding:9px 11px;border:1px solid #F0D69A;border-radius:7px;font-family:'DM Sans',sans-serif;font-size:14px;background:white;outline:none;margin-bottom:7px}
.focus-input:focus{border-color:var(--sunrise-dark)}
.focus-form-row{display:flex;gap:7px}
.focus-save{padding:7px 16px;background:var(--sunrise-dark);color:white;border:none;border-radius:7px;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;cursor:pointer}
.focus-cancel{padding:7px 12px;background:none;border:1px solid #F0D69A;border-radius:7px;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--sunrise-dark);cursor:pointer}
.pool-sect{background:#F5EEFF;border:1px solid #D8C7F0;border-radius:var(--r);padding:14px 16px;margin-bottom:16px}
.pool-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:9px}
.pool-title{font-size:13px;font-weight:600;color:var(--voc);text-transform:uppercase;letter-spacing:0.08em}
.pool-desc{font-size:12px;color:var(--voc);opacity:0.85;margin-bottom:11px;line-height:1.5}
.pool-item{display:flex;align-items:flex-start;gap:9px;padding:9px 11px;background:white;border-radius:var(--rs);margin-bottom:7px;border:1px solid #E5D8F5}
.pool-body{flex:1}
.pool-text{font-size:14px;color:var(--text);line-height:1.4}
.pool-meta{font-size:12px;color:var(--muted);margin-top:3px}
.pool-actions{display:flex;gap:5px}
.pool-btn{background:none;border:1px solid var(--border);font-size:12px;padding:4px 9px;border-radius:12px;color:var(--muted);cursor:pointer;font-family:'DM Sans',sans-serif;white-space:nowrap;font-weight:500}
.pool-btn:hover{background:var(--al);color:var(--accent);border-color:var(--accent)}
.pool-del{background:none;border:none;color:var(--border);font-size:16px;cursor:pointer;padding:0 4px}
.vh{display:flex;align-items:center;gap:12px;margin-bottom:18px}
.vav{width:40px;height:40px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:14px;font-weight:600;flex-shrink:0}
.vt{font-family:'DM Serif Display',serif;font-size:22px;font-weight:400}
.vs{font-size:13px;color:var(--muted);margin-top:2px}
.slbl2{font-size:12px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);font-weight:600;margin:20px 0 11px}
.card{background:white;border:1px solid var(--border);border-radius:var(--r);padding:16px 18px;margin-bottom:11px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.card.unread{border-left:3px solid var(--danger)}
.card.flash{animation:flash 1.4s ease}
@keyframes flash{0%{background:var(--al)}100%{background:white}}
.ct{display:flex;align-items:flex-start;gap:11px}
.cn{font-weight:600;font-size:17px;flex:1;line-height:1.4}
.cm{display:flex;align-items:center;gap:7px;margin-top:9px;flex-wrap:wrap}
.cb{font-size:12px;font-weight:600;padding:3px 9px;border-radius:20px}
.cb-Events{background:var(--evb);color:var(--evc)}
.cb-Projects{background:var(--prb);color:var(--prc)}
.cb-Administrative{background:var(--adb);color:var(--adc)}
.cb-Volunteer{background:var(--vob);color:var(--voc)}
.ow{font-size:12px;color:var(--muted);display:flex;align-items:center;gap:5px}
.owdot{width:20px;height:20px;border-radius:50%;background:var(--s2);border:1px solid var(--border);font-size:10px;font-weight:600;display:flex;align-items:center;justify-content:center;color:var(--text)}
.ts{font-size:12px;color:var(--muted);margin-left:auto}
.dr{display:flex;align-items:center;gap:8px;margin-top:9px;flex-wrap:wrap}
.dc{display:inline-flex;align-items:center;gap:5px;font-size:12px;padding:4px 9px;border-radius:20px;font-weight:500}
.dc.age{background:var(--s2);color:var(--muted)}
.dc.age.old{background:var(--sunrise-light);color:var(--sunrise-dark)}
.dc.age.stale{background:var(--dl);color:var(--danger)}
.dc.due{background:var(--al);color:var(--accent)}
.dc.soon{background:var(--wl);color:var(--warn)}
.dc.overdue{background:var(--dl);color:var(--danger);font-weight:600}
.dc.today{background:var(--sunrise-light);color:var(--sunrise-dark);font-weight:600}
.stog{display:flex;gap:5px;margin-top:11px}
.sbtn{flex:1;padding:8px 4px;font-size:12px;font-weight:600;border-radius:7px;border:1px solid var(--border);background:var(--bg);color:var(--muted);cursor:pointer;font-family:'DM Sans',sans-serif;text-align:center}
.sbtn.not{background:var(--s2);color:var(--text);border-color:var(--border)}
.sbtn.prog{background:var(--wl);color:var(--warn);border-color:var(--warn)}
.sbtn.done{background:var(--al);color:var(--accent);border-color:var(--accent)}
.delbtn{background:none;border:none;color:var(--border);font-size:20px;cursor:pointer;padding:2px 4px;line-height:1;font-family:'DM Sans',sans-serif}
.ns{margin-top:11px;border-top:1px solid var(--s2);padding-top:11px}
.nl{font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);font-weight:600;margin-bottom:7px;display:flex;align-items:center;gap:7px}
.ubadge{display:inline-flex;align-items:center;justify-content:center;min-width:18px;height:18px;border-radius:9px;font-size:11px;font-weight:700;padding:0 5px;background:var(--danger);color:white;animation:pulse 2s infinite}
.nd{font-size:14px;color:var(--muted);line-height:1.5;border-left:2px solid var(--border);padding-left:11px;cursor:pointer;min-height:22px}
.nd:hover{border-left-color:var(--accent);color:var(--text)}
.ne{width:100%;padding:9px 11px;border:1px solid var(--accent);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:white;resize:vertical;min-height:64px;outline:none;display:none}
.nea{display:none;gap:7px;margin-top:7px}
.nsave{padding:6px 16px;background:var(--accent);color:white;border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;cursor:pointer}
.ncanc{padding:6px 12px;background:none;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:13px;color:var(--muted);cursor:pointer}
.cs{margin-top:11px;border-top:1px solid var(--s2);padding-top:11px}
.ci{display:flex;gap:9px;margin-bottom:9px;align-items:flex-start}
.ci.u .cdot{background:var(--danger)}
.ci.u .ctxt{font-weight:500}
.cdot{width:7px;height:7px;border-radius:50%;background:var(--border);flex-shrink:0;margin-top:6px}
.cbdy{flex:1}
.ctxt{font-size:14px;color:var(--text);line-height:1.45}
.cmeta{font-size:12px;color:var(--muted);margin-top:3px}
.cauth{font-weight:600;color:var(--text)}
.ciw{margin-top:9px;background:var(--bg);border:1px solid var(--border);border-radius:var(--rs);padding:11px 13px}
.car{display:flex;align-items:center;gap:9px;margin-bottom:9px}
.cal{font-size:12px;color:var(--muted);white-space:nowrap}
.cas{flex:1;padding:6px 9px;border:1px solid var(--border);border-radius:7px;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);background:white;appearance:none;-webkit-appearance:none;outline:none}
.cir{display:flex;gap:7px}
.cin{flex:1;padding:9px 11px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:white;outline:none;resize:none;min-height:38px}
.cin:focus{border-color:var(--accent)}
.csub{padding:9px 14px;background:var(--accent);color:white;border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;cursor:pointer;white-space:nowrap;align-self:flex-end}
.exbtn{font-size:12px;color:var(--accent);background:none;border:none;cursor:pointer;font-family:'DM Sans',sans-serif;padding:5px 0;display:block;font-weight:600}
[data-theme="dark"]{--bg:#111820;--surface:#1A2330;--s2:#1F2D3D;--border:#2E3D4E;--text:#E8EDF2;--muted:#7A90A4;--accent:#6B96C4;--accent-dark:#5279A0;--al:#1A2D40;--sand:#111820;--sand-soft:#1A2330;--sand-deep:#1F2D3D;--tide-light:#0E2A2B;--sunrise-light:#2A1F00;}
[data-theme="dark"] .hdr{background:linear-gradient(155deg,#1F3550 0%,#152540 70%,#0E2A2B 100%)}
[data-theme="dark"] .focus-banner{background:linear-gradient(135deg,#2A1F00 0%,#1F1800 100%);border-color:#5A4010}
[data-theme="dark"] .focus-title{color:var(--sunrise)}
[data-theme="dark"] .fr input,[data-theme="dark"] .fr select,[data-theme="dark"] .fr textarea,[data-theme="dark"] .mform input,[data-theme="dark"] .mform select,[data-theme="dark"] .notesta,[data-theme="dark"] .bpa{background:var(--s2);color:var(--text);border-color:var(--border)}
[data-theme="dark"] .tabs,[data-theme="dark"] .syncbar{background:var(--surface);border-color:var(--border)}
[data-theme="dark"] .pool-sect{background:#1A1030;border-color:#3A2060}
[data-theme="dark"] .ciw{background:var(--s2)}
[data-theme="dark"] .ai{background:var(--s2)}
[data-theme="dark"] .search-input:focus{background:var(--s2)}
[data-theme="dark"] .card-compact,[data-theme="dark"] .card,[data-theme="dark"] .mp,[data-theme="dark"] .rs,[data-theme="dark"] .ap,[data-theme="dark"] .cal-card,[data-theme="dark"] .cal-detail-card,[data-theme="dark"] .cal-clock-big,[data-theme="dark"] .feed-card,[data-theme="dark"] .sc{background:var(--surface);border-color:var(--border)}
[data-theme="dark"] .ai-agenda-output{background:var(--surface)}
[data-theme="dark"] .ai-agenda-item{background:var(--s2)}
.dark-btn{background:rgba(255,255,255,0.15);border:1.5px solid rgba(255,255,255,0.3);color:white;font-size:15px;width:36px;height:36px;border-radius:50%;cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.search-wrap{position:relative;margin-bottom:14px}
.search-input{width:100%;padding:11px 14px 11px 40px;border:1px solid var(--border);border-radius:var(--r);font-family:'DM Sans',sans-serif;font-size:15px;color:var(--text);background:var(--surface);outline:none;transition:border-color 0.15s}
.search-input:focus{border-color:var(--accent)}
.search-icon{position:absolute;left:13px;top:50%;transform:translateY(-50%);font-size:16px;pointer-events:none;opacity:0.4}
.search-clear{position:absolute;right:12px;top:50%;transform:translateY(-50%);background:none;border:none;font-size:20px;color:var(--muted);cursor:pointer;padding:0;line-height:1;display:none}
.filter-bar{display:flex;gap:7px;margin-bottom:14px;flex-wrap:wrap}
.filter-btn{padding:6px 13px;border:1.5px solid var(--border);border-radius:20px;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;color:var(--muted);background:var(--surface);cursor:pointer;transition:all 0.15s}
.filter-btn.active{background:var(--accent);color:white;border-color:var(--accent)}
.filter-btn.warn-active{background:var(--danger);color:white;border-color:var(--danger)}
.filter-btn.sun-active{background:var(--sunrise);color:var(--sunrise-dark);border-color:var(--sunrise)}
.batch-bar{display:none;position:sticky;bottom:12px;z-index:100;background:var(--accent);color:white;border-radius:var(--r);padding:12px 16px;margin-top:10px;box-shadow:0 4px 16px rgba(31,53,80,0.3);align-items:center;gap:10px}
.batch-bar.show{display:flex}
.batch-bar-label{flex:1;font-size:14px;font-weight:600}
.batch-bar-btn{padding:8px 16px;border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:700;cursor:pointer}
.batch-bar-btn.done{background:white;color:var(--accent)}
.batch-bar-btn.cancel{background:rgba(255,255,255,0.2);color:white}
.card-checkbox{width:22px;height:22px;border-radius:6px;border:2px solid var(--border);background:white;flex-shrink:0;cursor:pointer;display:none;align-items:center;justify-content:center;font-size:14px;color:var(--accent);transition:all 0.15s}
.card-checkbox.show{display:flex}
.card-checkbox.checked{background:var(--accent);border-color:var(--accent);color:white}
.pin-btn{background:none;border:none;font-size:16px;cursor:pointer;padding:0 3px;line-height:1;opacity:0.3;transition:all 0.15s}
.pin-btn:hover{opacity:0.7}
.pin-btn.pinned{opacity:1}
.overdue-banner-wrap{background:var(--dl);border:1px solid #F5C0C0;border-radius:var(--r);padding:13px 15px;margin-bottom:16px}
.overdue-banner-hdr{font-size:12px;font-weight:700;color:var(--danger);text-transform:uppercase;letter-spacing:0.1em;margin-bottom:9px;display:flex;align-items:center;gap:6px}
.overdue-row{display:flex;align-items:center;justify-content:space-between;padding:8px 11px;background:white;border-radius:var(--rs);margin-bottom:5px;cursor:pointer;border:1px solid #F5C0C0}
.overdue-row:last-child{margin-bottom:0}
.overdue-row:hover{background:#FBDDDD}
.overdue-row-name{font-weight:600;font-size:14px;color:var(--text);flex:1}
.overdue-days{font-size:12px;font-weight:700;color:var(--danger);white-space:nowrap;margin-left:8px}
.feed-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:13px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.feed-card h3{font-family:'DM Serif Display',serif;font-size:20px;font-weight:400;margin-bottom:15px;padding-bottom:10px;border-bottom:1px solid var(--s2)}
.feed-item{display:flex;gap:11px;padding:10px 0;border-bottom:1px solid var(--s2);align-items:flex-start}
.feed-item:last-child{border-bottom:none;padding-bottom:0}
.feed-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0;margin-top:5px}
.feed-dot.new-task{background:var(--accent)}
.feed-dot.status-change{background:var(--warn)}
.feed-dot.completed{background:#3D8B5A}
.feed-dot.comment{background:var(--tide)}
.feed-dot.pinned{background:var(--sunrise-dark)}
.feed-body{flex:1}
.feed-text{font-size:14px;color:var(--text);line-height:1.4}
.feed-meta{font-size:12px;color:var(--muted);margin-top:3px}
.feed-empty{text-align:center;padding:32px;color:var(--muted);font-size:15px;font-style:italic}
.rec-badge{font-size:11px;padding:2px 8px;border-radius:20px;background:var(--prb);color:var(--prc);font-weight:600}
.ai-gen-card{background:linear-gradient(155deg,var(--accent) 0%,var(--accent-dark) 70%,var(--tide-dark) 100%);border-radius:var(--r);padding:20px;margin-bottom:14px;position:relative;overflow:hidden}
.ai-gen-card::before{content:'';position:absolute;top:-50px;right:-50px;width:160px;height:160px;border-radius:50%;background:radial-gradient(circle,var(--sunrise) 0%,transparent 70%);opacity:0.3;pointer-events:none}
.ai-gen-title{font-family:'DM Serif Display',serif;font-size:20px;color:white;margin-bottom:5px;position:relative}
.ai-gen-sub{font-size:13px;color:rgba(255,255,255,0.75);margin-bottom:16px;line-height:1.5;position:relative}
.ai-gen-btn{width:100%;padding:13px;background:var(--sunrise);color:var(--sunrise-dark);border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:15px;font-weight:700;cursor:pointer;position:relative;transition:all 0.15s}
.ai-gen-btn:hover{background:#F0B43A;transform:translateY(-1px)}
.ai-gen-btn:disabled{opacity:0.6;cursor:not-allowed;transform:none}
.ai-agenda-output{background:white;border-radius:var(--r);padding:18px;margin-bottom:14px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.ai-agenda-output h3{font-family:'DM Serif Display',serif;font-size:19px;margin-bottom:14px;padding-bottom:10px;border-bottom:1px solid var(--s2);color:var(--accent-dark)}
.ai-agenda-section{margin-bottom:18px}
.ai-agenda-section:last-child{margin-bottom:0}
.ai-agenda-section-title{font-size:12px;font-weight:700;text-transform:uppercase;letter-spacing:0.1em;color:var(--muted);margin-bottom:9px;padding-bottom:5px;border-bottom:1px solid var(--s2)}
.ai-agenda-item{padding:10px 13px;background:var(--bg);border-radius:var(--rs);margin-bottom:7px;border-left:3px solid var(--accent)}
.ai-agenda-item.urgent{border-left-color:var(--danger);background:var(--dl)}
.ai-agenda-item.focus{border-left-color:var(--sunrise-dark);background:var(--sunrise-light)}
.ai-agenda-item.info{border-left-color:var(--tide);background:var(--tide-light)}
.ai-agenda-item-title{font-size:14px;font-weight:600;color:var(--text);margin-bottom:3px}
.ai-agenda-item-detail{font-size:13px;color:var(--muted);line-height:1.45}
.ai-agenda-raw{font-size:14px;color:var(--text);line-height:1.7;white-space:pre-wrap}
.card-compact{background:white;border:1px solid var(--border);border-radius:var(--r);margin-bottom:7px;box-shadow:0 1px 3px rgba(31,53,80,0.05);overflow:hidden;transition:box-shadow 0.15s}
.card-compact.unread{border-left:3px solid var(--danger)}
.card-compact.flash{animation:flash 1.4s ease}
.card-compact:hover{box-shadow:0 2px 8px rgba(31,53,80,0.1)}
.card-compact-row{display:flex;align-items:center;gap:10px;padding:12px 14px;cursor:pointer;user-select:none;-webkit-user-select:none}
.card-status-bar{width:4px;height:36px;border-radius:3px;flex-shrink:0}
.card-status-bar.not{background:var(--border)}
.card-status-bar.prog{background:var(--warn)}
.card-status-bar.done{background:var(--accent)}
.card-compact-name{font-size:15px;font-weight:600;color:var(--text);flex:1;line-height:1.3;min-width:0;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.card-compact-name.done-text{text-decoration:line-through;color:var(--muted)}
.card-compact-meta{display:flex;align-items:center;gap:6px;flex-shrink:0}
.card-compact-chevron{font-size:16px;color:var(--muted);transition:transform 0.2s;flex-shrink:0;line-height:1}
.card-compact.open .card-compact-chevron{transform:rotate(90deg)}
.card-body{display:none;padding:0 14px 14px 14px;border-top:1px solid var(--s2)}
.card-compact.open .card-body{display:block}
.card-body-inner{padding-top:12px}
.obanner{background:var(--dl);border:1px solid #f5c0c0;border-radius:var(--rs);padding:11px 15px;font-size:13px;color:var(--danger);margin-bottom:18px;line-height:1.5}
.ap{background:white;border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:18px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.ap h3{font-family:'DM Serif Display',serif;font-size:19px;font-weight:400;margin-bottom:16px}
.fr{margin-bottom:13px}
.fr label{font-size:12px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:6px;font-weight:600}
.fr input,.fr select,.fr textarea{width:100%;padding:11px 13px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:15px;color:var(--text);background:var(--bg);appearance:none;-webkit-appearance:none;outline:none}
.fr textarea{resize:vertical;min-height:78px}
.fr input:focus,.fr select:focus,.fr textarea:focus{border-color:var(--accent);background:white}
.fg{display:grid;grid-template-columns:1fr 1fr;gap:11px}
.abtn{width:100%;padding:14px;background:var(--accent);color:white;border:none;border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:16px;font-weight:600;cursor:pointer;margin-top:5px}
.abtn:disabled{opacity:0.5}
.abtn:active{transform:scale(0.98)}
.modetog{display:flex;margin-bottom:15px;border:1px solid var(--border);border-radius:var(--rs);overflow:hidden}
.modebtn{flex:1;padding:10px;font-size:14px;font-weight:600;font-family:'DM Sans',sans-serif;border:none;background:var(--bg);color:var(--muted);cursor:pointer}
.modebtn.on{background:var(--accent);color:white}
.bpa{width:100%;min-height:130px;padding:11px 13px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--bg);resize:vertical;outline:none;line-height:1.7}
.bpa:focus{border-color:var(--accent);background:white}
.btbl{width:100%;border-collapse:collapse;font-size:14px}
.btbl th{font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);font-weight:600;padding:7px 4px;text-align:left;border-bottom:1px solid var(--border)}
.btbl td{padding:6px 4px;border-bottom:1px solid var(--s2);vertical-align:middle}
.btbl tr:last-child td{border-bottom:none}
.btn-name{padding:5px 7px;border:1px solid var(--border);border-radius:5px;font-family:'DM Sans',sans-serif;font-size:13px;width:100%;outline:none;background:white}
.bsel{width:100%;padding:5px 7px;border:1px solid var(--border);border-radius:5px;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);background:var(--bg);appearance:none;-webkit-appearance:none;outline:none}
.brem{background:none;border:none;color:var(--border);font-size:18px;cursor:pointer;padding:2px 4px;font-family:'DM Sans',sans-serif}
.bcount{font-size:13px;color:var(--muted);margin-bottom:11px}
.rs{background:white;border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:13px}
.rs h3{font-family:'DM Serif Display',serif;font-size:19px;font-weight:400;margin-bottom:15px;padding-bottom:11px;border-bottom:1px solid var(--border)}
.rr{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--s2);font-size:14px}
.rr:last-child{border-bottom:none}
.rbadge{font-size:12px;font-weight:600;padding:3px 9px;border-radius:20px}
.bnot{background:var(--s2);color:var(--muted)}
.bprog{background:var(--wl);color:var(--warn)}
.bdone{background:var(--al);color:var(--accent)}
.mblk{margin-bottom:15px}
.mhdr{display:flex;align-items:center;gap:9px;margin-bottom:9px}
.mavs{width:30px;height:30px;border-radius:50%;font-size:12px;font-weight:600;display:flex;align-items:center;justify-content:center}
.mname{font-weight:600;font-size:15px}
.mcnt{font-size:13px;color:var(--muted)}
.mp{background:white;border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:13px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.mp-title{font-family:'DM Serif Display',serif;font-size:20px;font-weight:400;color:var(--text);margin-bottom:5px}
.mp-sub{font-size:13px;color:var(--muted);margin-bottom:15px}
.msel{padding:10px 13px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--bg);appearance:none;-webkit-appearance:none;outline:none;width:100%;margin-bottom:11px}
.msel:focus{border-color:var(--accent)}
.new-mtg-btn{width:100%;padding:12px;border:1px dashed var(--border);border-radius:var(--rs);font-family:'DM Serif Display',serif;font-size:16px;font-weight:400;color:var(--muted);background:none;cursor:pointer;margin-bottom:13px}
.new-mtg-btn:hover{border-color:var(--accent);color:var(--accent)}
.mform{background:var(--bg);border:1px solid var(--border);border-radius:var(--rs);padding:14px;margin-top:11px;display:none}
.mform input,.mform select{width:100%;padding:10px 13px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:15px;color:var(--text);background:white;appearance:none;-webkit-appearance:none;outline:none;margin-bottom:9px}
.mform input:focus,.mform select:focus{border-color:var(--accent)}
.mform label{font-size:12px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px;font-weight:600}
.fbtnrow{display:flex;gap:9px;margin-top:5px}
.fbtn{padding:9px 17px;border-radius:var(--rs);border:none;font-family:'DM Sans',sans-serif;font-size:14px;font-weight:600;cursor:pointer}
.fbtn.p{background:var(--accent);color:white}
.fbtn.s{background:var(--s2);color:var(--text);border:1px solid var(--border)}
.ai{display:flex;align-items:flex-start;gap:11px;padding:11px 13px;background:var(--bg);border:1px solid var(--border);border-radius:var(--rs);margin-bottom:9px}
.ai.done .ait{text-decoration:line-through;opacity:0.5}
.aichk{width:22px;height:22px;border-radius:5px;border:1px solid var(--border);background:white;cursor:pointer;flex-shrink:0;margin-top:2px;display:flex;align-items:center;justify-content:center;font-size:13px}
.aichk.on{background:var(--al);border-color:var(--accent);color:var(--accent)}
.aibdy{flex:1}
.ait{font-size:15px;font-weight:600;color:var(--text);line-height:1.4}
.aidet{font-size:14px;color:var(--muted);margin-top:5px;line-height:1.45}
.aimeta{font-size:12px;color:var(--muted);margin-top:4px}
.mrow{display:flex;align-items:center;justify-content:space-between;padding:13px 0;border-bottom:1px solid var(--s2);cursor:pointer}
.mrow:last-child{border-bottom:none}
.mrow-t{font-weight:600;font-size:15px}
.mrow-m{font-size:13px;color:var(--muted)}
.backbtn{display:flex;align-items:center;gap:7px;font-size:14px;color:var(--accent);cursor:pointer;margin-bottom:18px;background:none;border:none;font-family:'DM Sans',sans-serif;padding:0;font-weight:600}
.div{height:1px;background:var(--border);margin:18px 0}
.notesta{width:100%;min-height:130px;padding:11px 13px;border:1px solid var(--border);border-radius:var(--rs);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--bg);resize:vertical;outline:none;line-height:1.65}
.notesta:focus{border-color:var(--accent);background:white}
.attlist{margin-top:11px;display:flex;flex-wrap:wrap;gap:8px}
.attchip{display:inline-flex;align-items:center;gap:7px;padding:6px 11px;background:var(--prb);color:var(--prc);border-radius:20px;font-size:13px;font-weight:600;text-decoration:none}
.uparea{border:1px dashed var(--border);border-radius:var(--rs);padding:16px;text-align:center;font-size:13px;color:var(--muted);cursor:pointer;margin-top:11px}
.uparea:hover{border-color:var(--accent);color:var(--accent)}
.clbanner{font-size:12px;color:var(--warn);background:var(--wl);padding:9px 11px;border-radius:var(--rs);margin-bottom:11px;line-height:1.6;display:none}
.cal-clock-big{background:linear-gradient(155deg,var(--accent) 0%,var(--accent-dark) 65%,var(--tide-dark) 100%);color:white;border-radius:var(--r);padding:24px 22px;margin-bottom:16px;box-shadow:0 4px 14px rgba(31,53,80,0.12);position:relative;overflow:hidden}
.cal-clock-big::before{content:'';position:absolute;top:-70px;right:-70px;width:200px;height:200px;border-radius:50%;background:radial-gradient(circle,var(--sunrise) 0%,transparent 70%);opacity:0.3;pointer-events:none}
.cal-clock-label{font-size:11px;font-weight:600;letter-spacing:0.18em;text-transform:uppercase;color:var(--sunrise-light);position:relative;margin-bottom:6px}
.cal-clock-time{font-family:'DM Serif Display',serif;font-size:48px;font-weight:400;line-height:1;font-variant-numeric:tabular-nums;letter-spacing:-0.02em;position:relative}
.cal-clock-sec{font-size:22px;color:var(--sunrise);margin-left:5px;vertical-align:top;position:relative;top:0.25em}
.cal-clock-mer{font-size:18px;font-weight:400;color:var(--sunrise);margin-left:5px;letter-spacing:0.04em}
.cal-clock-date{font-size:14px;opacity:0.92;margin-top:8px;font-style:italic;font-family:'DM Serif Display',serif;position:relative}
.cal-clock-day{display:inline-block;font-style:normal;font-family:'DM Sans',sans-serif;font-weight:600;text-transform:uppercase;letter-spacing:0.16em;font-size:11px;color:var(--sunrise);margin-right:8px}
.cal-card{background:white;border:1px solid var(--border);border-radius:var(--r);padding:18px;margin-bottom:14px;box-shadow:0 1px 3px rgba(31,53,80,0.06)}
.cal-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:13px}
.cal-title{font-family:'DM Serif Display',serif;font-size:21px;color:var(--accent-dark);letter-spacing:-0.01em}
.cal-title em{color:var(--tide-dark);font-style:italic;font-weight:300}
.cal-nav{width:38px;height:38px;border-radius:50%;border:1.5px solid var(--tide);background:white;color:var(--accent-dark);font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center;font-family:'DM Sans',sans-serif;transition:all 0.18s}
.cal-nav:hover{background:var(--tide);color:white;border-color:var(--tide)}
.cal-today-btn-row{display:flex;justify-content:center;margin-bottom:11px}
.cal-today-btn{padding:6px 16px;background:var(--sunrise);color:var(--sunrise-dark);border:none;border-radius:20px;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:700;letter-spacing:0.08em;text-transform:uppercase;cursor:pointer}
.cal-today-btn:hover{background:#F0B43A}
.cal-weekdays{display:grid;grid-template-columns:repeat(7,1fr);gap:5px;margin-bottom:7px}
.cal-weekdays span{text-align:center;font-size:11px;color:var(--muted);font-weight:700;text-transform:uppercase;letter-spacing:0.1em;padding:4px 0}
.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:5px}
.cal-day{aspect-ratio:1;display:flex;flex-direction:column;align-items:center;justify-content:center;font-size:15px;font-weight:500;border-radius:9px;border:1.5px solid transparent;background:var(--sand-soft);color:var(--text);cursor:pointer;font-family:'DM Sans',sans-serif;position:relative;padding:0;transition:all 0.15s}
.cal-day:hover:not(.empty){background:var(--tide-light);transform:translateY(-1px)}
.cal-day.empty{background:transparent;cursor:default;border:none}
.cal-day.today{background:var(--sunrise);color:var(--sunrise-dark);font-weight:700;box-shadow:0 3px 10px rgba(244,190,81,0.35)}
.cal-day.selected{border-color:var(--accent);background:var(--al);color:var(--accent-dark);font-weight:700}
.cal-day.today.selected{border-color:var(--accent-dark);background:var(--sunrise);color:var(--sunrise-dark)}
.cal-day-num{line-height:1.1}
.cal-dots{display:flex;gap:2px;margin-top:2px;height:6px}
.cal-dot{display:inline-block;width:5px;height:5px;border-radius:50%}
.cal-legend{display:flex;justify-content:center;gap:14px;margin-top:13px;font-size:12px;color:var(--muted);flex-wrap:wrap;padding-top:12px;border-top:1px solid var(--s2)}
.cal-leg-dot{display:inline-block;width:7px;height:7px;border-radius:50%;margin-right:5px;vertical-align:middle}
.cal-detail-card{background:white;border:1px solid var(--border);border-radius:var(--r);padding:18px;box-shadow:0 1px 3px rgba(31,53,80,0.06);margin-bottom:14px}
.cal-detail-title{font-family:'DM Serif Display',serif;font-size:19px;margin-bottom:13px;padding-bottom:9px;border-bottom:1px solid var(--s2);color:var(--accent-dark)}
.cal-detail-empty{font-size:14px;color:var(--muted);font-style:italic;padding:18px 0;text-align:center}
.cal-detail-section{margin-bottom:15px}
.cal-detail-section:last-child{margin-bottom:0}
.cal-detail-label{font-size:11px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);margin-bottom:7px;font-weight:700}
.cal-detail-item{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;background:var(--bg);border-radius:var(--rs);margin-bottom:7px;border:1px solid var(--border);gap:10px}
.cal-detail-item:last-child{margin-bottom:0}
.cal-detail-item.meeting{border-left:3px solid var(--tide);cursor:pointer}
.cal-detail-item.meeting:hover{background:var(--tide-light)}
.cal-detail-item-name{font-size:15px;font-weight:600;color:var(--text)}
.cal-detail-item-meta{font-size:12px;color:var(--muted);margin-top:3px}
.empty{text-align:center;padding:36px 22px;color:var(--muted);font-size:15px}
.bpad{height:48px}
</style>
</head>
<body>
<div id="settingsOverlay">
  <div class="so-title">Settings</div>
  <div class="so-sub">CCFWB Team App</div>
  <div class="so-card">
    <div class="so-label">JSONBin — Bin ID</div>
    <div class="so-value" id="so-db-url">Not connected</div>
    <button class="so-btn green" onclick="copyDbUrl()">Copy Bin ID for teammates</button>
  </div>
  <div class="so-card">
    <div class="so-label">Cloudinary — file uploads</div>
    <p style="font-size:13px;color:rgba(255,255,255,0.6);margin-bottom:11px;line-height:1.6">Get a free account at cloudinary.com then enter your Cloud Name and Upload Preset below.</p>
    <input class="so-input" type="text" id="so-cloud" placeholder="Cloud Name (e.g. dxxxxxxx)" />
    <input class="so-input" type="text" id="so-preset" placeholder="Upload Preset name" />
    <button class="so-btn green" onclick="saveCloudinary()">Save</button>
    <span class="so-saved" id="so-saved">Saved ✓</span>
  </div>
  <div class="so-card">
    <div class="so-label">Reset app</div>
    <p style="font-size:13px;color:rgba(255,255,255,0.6);margin-bottom:11px">Clears your connection. Your data in JSONBin is not deleted.</p>
    <button class="so-btn red" onclick="doReset()">Reset app</button>
  </div>
  <button class="so-close" onclick="closeSettings()">← Back to App</button>
</div>
<div class="setup" id="setup">
  <div class="setup-logo">CCFWB<br>Team</div>
  <div class="setup-sub">One-time setup</div>
  <div class="setup-card">
    <h3>Connect to JSONBin</h3>
    <p>Paste your JSONBin Bin ID and Master Key below. Share these same values with teammates so everyone stays in sync.</p>
    <label style="font-size:12px;color:var(--muted);display:block;margin-bottom:5px">Bin ID</label>
    <input class="si" type="text" id="dbInput" placeholder="e.g. 65f3a2b1e41b4d34f807c9a2" />
    <label style="font-size:12px;color:var(--muted);display:block;margin-bottom:5px">X-Master-Key</label>
    <input class="si" type="text" id="apiKeyInput" placeholder="$2a$10$..." />
    <button class="sb" id="connectBtn" onclick="connectJsonBin()">Connect &amp; Sync</button>
    <div class="scopy" id="urlBox" onclick="copySetupUrl()"></div>
    <div class="serr" id="setupErr"></div>
  </div>
  <button class="sbo" onclick="demoMode()">Skip — use offline demo mode</button>
</div>
<div class="loader gone" id="loader"><div class="spin"></div><span id="loaderMsg">Loading...</span></div>
<div class="notif" id="notif"><div class="ndot"></div><span id="notifTxt">Synced</span></div>
<div class="hdr" id="hdr" style="display:none">
  <div class="hdr-sub">Calvary Chapel Fort Walton Beach</div>
  <h1>Team</h1>
  <div class="hdr-row">
    <div class="hdr-stat" id="hdrStat">—</div>
    <div class="hdr-clock" id="hdrClock">— : —</div>
    <button class="dark-btn" id="darkBtn" onclick="toggleDark()" title="Toggle dark mode">🌙</button>
    <button class="settings-btn" id="settingsBtn" onclick="openSettings()">⚙</button>
  </div>
</div>
<div class="syncbar" id="syncbar" style="display:none">
  <div class="sdot" id="sdot"></div>
  <span class="slbl" id="slbl">Connecting...</span>
  <button class="sact" onclick="syncNow()">Refresh</button>
</div>
<div id="tabbar" style="display:none">
  <div class="tabs">
    <button class="tab on" id="tb-Andy" onclick="go('Andy')">Pastor Andy<span class="tc" id="tc-Andy">0</span></button>
    <button class="tab" id="tb-Kaitlyn" onclick="go('Kaitlyn')">Kaitlyn<span class="tc" id="tc-Kaitlyn">0</span></button>
    <button class="tab" id="tb-Angie" onclick="go('Angie')">Angie<span class="tc" id="tc-Angie">0</span></button>
    <div class="tdiv"></div>
    <button class="tab" id="tb-Events" onclick="go('Events')">Events<span class="tc" id="tc-Events">0</span></button>
    <button class="tab" id="tb-Volunteer" onclick="go('Volunteer')">Volunteers<span class="tc" id="tc-Volunteer">0</span></button>
    <button class="tab" id="tb-Projects" onclick="go('Projects')">Projects<span class="tc" id="tc-Projects">0</span></button>
    <div class="tdiv"></div>
    <button class="tab" id="tb-orphaned" onclick="go('orphaned')">Orphaned<span class="tc d" id="tc-orphaned">0</span></button>
    <div class="tdiv"></div>
    <button class="tab" id="tb-agenda" onclick="go('agenda')">Agenda<span class="tc a" id="tc-agenda">0</span></button>
    <button class="tab" id="tb-meetings" onclick="go('meetings')">Meetings</button>
    <button class="tab" id="tb-calendar" onclick="go('calendar')">📅 Calendar</button>
    <button class="tab" id="tb-feed" onclick="go('feed')">📡 Feed</button>
    <div class="tdiv"></div>
    <button class="tab" id="tb-add" onclick="go('add')">+ Add</button>
    <button class="tab" id="tb-report" onclick="go('report')">Report</button>
  </div>
</div>
<div class="main" id="main" style="display:none">
  <div id="pv-view">
    <div id="focus-area"></div>
    <div id="vh-area"></div>
    <div class="search-wrap" id="search-wrap" style="display:none">
      <span class="search-icon">🔍</span>
      <input class="search-input" id="searchInput" type="text" placeholder="Search tasks..." oninput="onSearch(this.value)" />
      <button class="search-clear" id="searchClear" onclick="clearSearch()">×</button>
    </div>
    <div class="filter-bar" id="filterBar" style="display:none">
      <button class="filter-btn active" id="fb-all" onclick="setFilter('all')">All</button>
      <button class="filter-btn" id="fb-quickwins" onclick="setFilter('quickwins')">⚡ Quick Wins</button>
      <button class="filter-btn" id="fb-pinned" onclick="setFilter('pinned')">📌 Pinned</button>
      <button class="filter-btn" id="fb-overdue" onclick="setFilter('overdue')">🔴 Overdue</button>
      <button class="filter-btn" id="fb-batch" onclick="toggleBatch()">☑ Select</button>
    </div>
    <div class="sg">
      <div class="sc"><div class="n n-t" id="c-todo">0</div><div class="l">Not Started</div></div>
      <div class="sc"><div class="n n-p" id="c-prog">0</div><div class="l">In Progress</div></div>
      <div class="sc"><div class="n n-d" id="c-done">0</div><div class="l">Complete</div></div>
    </div>
    <div id="vsections"></div>
    <div id="vempty" class="empty" style="display:none">No tasks here yet.</div>
    <div class="batch-bar" id="batchBar">
      <span class="batch-bar-label" id="batchLabel">0 selected</span>
      <button class="batch-bar-btn done" onclick="batchComplete()">✓ Mark Done</button>
      <button class="batch-bar-btn cancel" onclick="toggleBatch()">Cancel</button>
    </div>
  </div>
  <div id="pv-add" style="display:none">
    <div class="ap">
      <h3>Log a Task</h3>
      <div class="modetog">
        <button class="modebtn on" id="mb-single" onclick="setMode('single')">Single Task</button>
        <button class="modebtn" id="mb-bulk" onclick="setMode('bulk')">Bulk Add</button>
      </div>
      <div id="single-panel">
        <div class="fr"><label>Task Name</label><input type="text" id="i-name" placeholder="What needs to be done?" /></div>
        <div class="fg">
          <div class="fr"><label>Category</label>
            <select id="i-cat">
              <option value="Events">Events</option>
              <option value="Projects">Special Projects</option>
              <option value="Administrative">Administrative</option>
              <option value="Volunteer">Volunteer Management</option>
            </select>
          </div>
          <div class="fr"><label>Owner</label>
            <select id="i-owner">
              <option value="">— Unassigned —</option>
              <option value="Pastor Andy">Pastor Andy</option>
              <option value="Kaitlyn">Kaitlyn</option>
              <option value="Angie">Angie</option>
            </select>
          </div>
        </div>
        <div class="fr"><label>Status</label>
          <select id="i-status">
            <option value="not">Not Started</option>
            <option value="prog">In Progress</option>
            <option value="done">Complete</option>
          </select>
        </div>
        <div class="fr"><label>Target Date (optional)</label><input type="date" id="i-due" /></div>
        <div class="fr"><label>Recurring</label>
          <select id="i-recurring">
            <option value="none">One-time (no repeat)</option>
            <option value="weekly">Weekly — repeats every 7 days</option>
            <option value="monthly">Monthly — repeats every 30 days</option>
          </select>
        </div>
        <div class="fr"><label>Notes (optional)</label><textarea id="i-notes" placeholder="Any details..."></textarea></div>
        <button class="abtn" id="addBtn" onclick="addTask()">Add Task</button>
      </div>
      <div id="bulk-panel" style="display:none">
        <div id="bulk-paste">
          <div class="fr"><label>Paste tasks — one per line</label>
            <textarea class="bpa" id="bulk-input" placeholder="Call employer about job fair&#10;Update volunteer spreadsheet&#10;Schedule resume workshop"></textarea>
          </div>
          <button class="abtn" onclick="parseBulk()">Review Tasks →</button>
        </div>
        <div id="bulk-review" style="display:none">
          <div class="bcount" id="bcount"></div>
          <div style="overflow-x:auto">
            <table class="btbl">
              <thead><tr><th>Task</th><th>Owner</th><th>Category</th><th></th></tr></thead>
              <tbody id="btbody"></tbody>
            </table>
          </div>
          <div style="display:flex;gap:9px;margin-top:15px">
            <button class="abtn" id="bulkSaveBtn" onclick="saveBulk()">Save All Tasks</button>
            <button class="fbtn s" onclick="backToPaste()">← Edit</button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div id="pv-report" style="display:none"><div id="report-content"></div></div>
  <div id="pv-calendar" style="display:none">
    <div class="cal-clock-big">
      <div class="cal-clock-label">Right Now</div>
      <div class="cal-clock-time" id="bigClockTime">—</div>
      <div class="cal-clock-date">
        <span class="cal-clock-day" id="bigClockDay">—</span>
        <span id="bigClockDate">—</span>
      </div>
    </div>
    <div class="cal-card">
      <div class="cal-header">
        <button class="cal-nav" onclick="calPrev()">‹</button>
        <div class="cal-title" id="calMonthTitle">— <em>—</em></div>
        <button class="cal-nav" onclick="calNext()">›</button>
      </div>
      <div class="cal-today-btn-row"><button class="cal-today-btn" onclick="calToday()">Today</button></div>
      <div class="cal-weekdays">
        <span>Sun</span><span>Mon</span><span>Tue</span><span>Wed</span><span>Thu</span><span>Fri</span><span>Sat</span>
      </div>
      <div class="cal-grid" id="calGrid"></div>
      <div class="cal-legend">
        <span><span class="cal-leg-dot" style="background:var(--danger)"></span>Overdue</span>
        <span><span class="cal-leg-dot" style="background:var(--accent)"></span>Tasks Due</span>
        <span><span class="cal-leg-dot" style="background:var(--tide)"></span>Meeting</span>
      </div>
    </div>
    <div id="calDayDetail"></div>
  </div>
  <div id="pv-feed" style="display:none">
    <div class="feed-card">
      <h3>📡 Team Activity Feed</h3>
      <div id="feedList"><div class="feed-empty">No activity yet — start adding tasks!</div></div>
    </div>
  </div>
  <div id="pv-agenda" style="display:none">
    <div class="ai-gen-card">
      <div class="ai-gen-title">🤖 AI Agenda Generator</div>
      <div class="ai-gen-sub">Claude reads your tasks, overdue items, priorities, notes, and topic pool — then builds a ready-to-run meeting agenda ranked by urgency.</div>
      <button class="ai-gen-btn" id="aiGenBtn" onclick="generateAgenda()">✨ Generate Meeting Agenda</button>
    </div>
    <div id="ai-agenda-output" style="display:none"></div>
    <div class="mp">
      <div class="mp-title">Meeting Agenda</div>
      <div class="mp-sub">Add topics for the next meeting. Anyone on the team can contribute.</div>
      <select class="msel" id="agenda-sel" onchange="renderAgendaItems()">
        <option value="">— Select a meeting —</option>
      </select>
      <button class="new-mtg-btn" onclick="showMtgForm('agenda')">+ Schedule a new meeting</button>
      <div class="mform" id="mtg-form-agenda">
        <label>Meeting Date</label><input type="date" id="mf-date-agenda" />
        <label>Meeting Title (optional)</label><input type="text" id="mf-title-agenda" placeholder="e.g. Weekly Team Meeting" />
        <div class="fbtnrow">
          <button class="fbtn p" onclick="createMeeting('agenda')">Create Meeting</button>
          <button class="fbtn s" onclick="hideMtgForm('agenda')">Cancel</button>
        </div>
      </div>
    </div>
    <div class="pool-sect">
      <div class="pool-hdr">
        <div class="pool-title">💭 Topic Pool</div>
        <button class="fbtn p" style="padding:6px 13px;font-size:13px" onclick="showPoolForm()">+ Add Topic</button>
      </div>
      <div class="pool-desc">Drop topics here anytime. When you create a meeting you can pull these in.</div>
      <div class="mform" id="pool-form">
        <label>Topic</label><input type="text" id="pf-topic" placeholder="What should we discuss?" />
        <label>Details (optional)</label><input type="text" id="pf-details" placeholder="Background info..." />
        <label>Added by</label>
        <select id="pf-author">
          <option value="">— Select your name —</option>
          <option value="Pastor Andy">Pastor Andy</option>
          <option value="Kaitlyn">Kaitlyn</option>
          <option value="Angie">Angie</option>
        </select>
        <div class="fbtnrow">
          <button class="fbtn p" onclick="addPoolTopic()">Add to Pool</button>
          <button class="fbtn s" onclick="hidePoolForm()">Cancel</button>
        </div>
      </div>
      <div id="pool-list"></div>
      <div id="pool-empty" class="focus-empty" style="color:var(--voc);opacity:0.7">No topics in the pool yet.</div>
    </div>
    <div id="agenda-panel" style="display:none">
      <div class="mp">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:13px">
          <div>
            <div class="mp-title" id="agenda-title">Agenda</div>
            <div class="mp-sub" id="agenda-date"></div>
          </div>
          <button class="fbtn p" onclick="showTopicForm()">+ Add Topic</button>
        </div>
        <div class="mform" id="topic-form">
          <label>Topic</label><input type="text" id="tf-topic" placeholder="What do you want to discuss?" />
          <label>Details (optional)</label><input type="text" id="tf-details" placeholder="Background info..." />
          <label>Added by</label>
          <select id="tf-author">
            <option value="">— Select your name —</option>
            <option value="Pastor Andy">Pastor Andy</option>
            <option value="Kaitlyn">Kaitlyn</option>
            <option value="Angie">Angie</option>
          </select>
          <div class="fbtnrow">
            <button class="fbtn p" onclick="addTopic()">Add Topic</button>
            <button class="fbtn s" onclick="hideTopicForm()">Cancel</button>
          </div>
        </div>
        <div id="agenda-list" style="margin-top:13px"></div>
        <div id="agenda-empty" class="empty" style="display:none">No topics yet — be the first to add one.</div>
      </div>
    </div>
  </div>
  <div id="pv-meetings" style="display:none">
    <div id="mtg-list-view">
      <div class="mp">
        <div class="mp-title">Meeting Notes</div>
        <div class="mp-sub">Notes and attachments organized by meeting date. Tap a meeting to open it.</div>
        <button class="new-mtg-btn" onclick="showMtgForm('meetings')">+ Add a meeting</button>
        <div class="mform" id="mtg-form-meetings">
          <label>Meeting Date</label><input type="date" id="mf-date-meetings" />
          <label>Meeting Title (optional)</label><input type="text" id="mf-title-meetings" placeholder="e.g. Weekly Team Meeting" />
          <div class="fbtnrow">
            <button class="fbtn p" onclick="createMeeting('meetings')">Create Meeting</button>
            <button class="fbtn s" onclick="hideMtgForm('meetings')">Cancel</button>
          </div>
        </div>
        <div id="mtg-list"></div>
        <div id="mtg-empty" class="empty">No meetings yet.</div>
      </div>
    </div>
    <div id="mtg-detail-view" style="display:none">
      <button class="backbtn" onclick="closeMtgDetail()">← Back to meetings</button>
      <div class="mp">
        <div class="mp-title" id="dtl-title"></div>
        <div class="mp-sub" id="dtl-date"></div>
        <div class="div"></div>
        <div class="nl" style="margin-bottom:9px">Notes</div>
        <textarea class="notesta" id="dtl-notes" placeholder="Type meeting notes here..."></textarea>
        <button class="fbtn p" style="margin-top:9px" onclick="saveMtgNotes()">Save Notes</button>
        <div class="div"></div>
        <div class="nl" style="margin-bottom:9px">Attachments</div>
        <div class="clbanner" id="cl-banner">To enable file uploads tap ⚙ Settings and enter your Cloudinary details.</div>
        <div class="attlist" id="dtl-atts"></div>
        <label class="uparea" for="file-inp">📎 Tap to attach a photo or document</label>
        <input type="file" id="file-inp" style="display:none" accept="image/*,.pdf,.doc,.docx" onchange="uploadFile(event)" />
        <div id="up-prog" style="font-size:13px;color:var(--muted);margin-top:7px;display:none">Uploading...</div>
      </div>
    </div>
  </div>
  <div class="bpad"></div>
</div>
<script>
const CK='ccfwb_creds_v3';const LK='ccfwb_local_v3';const RK='ccfwb_read_v1';const POLL=15000;
let creds=null,tasks=[],meetings=[],focusItems=[],poolTopics=[],active='Andy',activeMtg=null,pollTimer=null,saving=false,notifTimer=null,readLog={};
let calViewMonth=new Date().getMonth(),calViewYear=new Date().getFullYear(),calSelected=null;
let activityLog=[],searchQuery='',filterMode='all',batchMode=false,batchSelected=new Set();
const PEOPLE=[
  {key:'Andy',label:'Pastor Andy',ini:'PA',col:'var(--anc)',bg:'var(--anb)',match:t=>om(t,'Andy')},
  {key:'Kaitlyn',label:'Kaitlyn',ini:'KA',col:'var(--kac)',bg:'var(--kab)',match:t=>om(t,'Kaitlyn')},
  {key:'Angie',label:'Angie',ini:'AN',col:'var(--agc)',bg:'var(--agb)',match:t=>om(t,'Angie')},
];
const CATS=[
  {key:'Events',label:'Events',col:'var(--evc)',bg:'var(--evb)'},
  {key:'Volunteer',label:'Volunteer Management',col:'var(--voc)',bg:'var(--vob)'},
  {key:'Projects',label:'Special Projects',col:'var(--prc)',bg:'var(--prb)'},
  {key:'Administrative',label:'Administrative',col:'var(--adc)',bg:'var(--adb)'},
];
const ALL_TABS=['Andy','Kaitlyn','Angie','Events','Volunteer','Projects','orphaned','agenda','meetings','calendar','feed','add','report'];
function om(t,k){return t.owner&&t.owner.toLowerCase().includes(k.toLowerCase())}
function loadRL(){try{readLog=JSON.parse(localStorage.getItem(RK))||{};}catch(e){readLog={};}}
function saveRL(){localStorage.setItem(RK,JSON.stringify(readLog));}
function markRead(id){readLog[id]=Date.now();saveRL();}
function unreadCnt(t){if(!t.comments||!t.comments.length)return 0;const l=readLog[t.id]||0;return t.comments.filter(c=>c.ts>l).length;}
function init(){
  loadRL();
  if(localStorage.getItem('ccfwb_dark')==='1'){document.documentElement.setAttribute('data-theme','dark');const db=document.getElementById('darkBtn');if(db)db.textContent='☀️';}
  try{creds=JSON.parse(localStorage.getItem(CK));}catch(e){creds=null;}
  if(creds){showApp();if(creds.demoMode){loadLocal();renderAll();setSS('demo','Offline demo mode');}else{syncNow(true);startPoll();}}
  tickClock();setInterval(tickClock,1000);setTimeout(checkRecurring,2000);
}
function showApp(){const s=document.getElementById('setup');if(s)s.classList.add('gone');['hdr','syncbar','tabbar','main'].forEach(id=>{const el=document.getElementById(id);if(el)el.style.display='';});}
function openSettings(){const o=document.getElementById('settingsOverlay');if(!o)return;const dbEl=document.getElementById('so-db-url');if(dbEl)dbEl.textContent=(creds&&creds.binId)?creds.binId:'Demo mode (no database)';const cn=document.getElementById('so-cloud');const cp=document.getElementById('so-preset');if(cn&&creds&&creds.cloudName)cn.value=creds.cloudName;if(cp&&creds&&creds.cloudPreset)cp.value=creds.cloudPreset;const sv=document.getElementById('so-saved');if(sv)sv.style.display='none';o.classList.add('open');}
function closeSettings(){const o=document.getElementById('settingsOverlay');if(o)o.classList.remove('open');}
function copyDbUrl(){const url=(creds&&creds.binId)?creds.binId:'';if(!url){showNotif('No Bin ID to copy');return;}try{navigator.clipboard.writeText(url);showNotif('Bin ID copied!');}catch(e){alert('Bin ID:\n'+url);}}
function saveCloudinary(){const cloud=(document.getElementById('so-cloud').value||'').trim();const preset=(document.getElementById('so-preset').value||'').trim();if(!cloud||!preset){showNotif('Please fill in both fields');return;}if(!creds)creds={};creds.cloudName=cloud;creds.cloudPreset=preset;localStorage.setItem(CK,JSON.stringify(creds));const sv=document.getElementById('so-saved');if(sv)sv.style.display='inline';showNotif('Cloudinary settings saved!');}
function doReset(){if(confirm('Reset the app? Your data in JSONBin will not be deleted.')){localStorage.removeItem(CK);location.reload();}}
async function connectJsonBin(){
  const binId=(document.getElementById('dbInput').value||'').trim().replace(/.*\/b\//,'').split('/')[0];
  const apiKey=(document.getElementById('apiKeyInput').value||'').trim();
  if(!binId){showErr('Please enter your Bin ID.');return;}
  if(!apiKey){showErr('Please enter your X-Master-Key.');return;}
  const btn=document.getElementById('connectBtn');btn.disabled=true;btn.textContent='Connecting...';
  document.getElementById('setupErr').style.display='none';
  try{
    const r=await fetch('https://api.jsonbin.io/v3/b/'+binId+'/latest',{headers:{'X-Master-Key':apiKey}});
    if(!r.ok)throw new Error('Could not read bin ('+r.status+') — check your Bin ID and Key');
    const j=await r.json();const d=j.record||{};
    tasks=(d.tasks)?Object.values(d.tasks):[];meetings=(d.meetings)?Object.values(d.meetings):[];focusItems=(d.focusItems)?Object.values(d.focusItems):[];poolTopics=(d.poolTopics)?Object.values(d.poolTopics):[];
    saveLocal();creds={binId,apiKey,demoMode:false};localStorage.setItem(CK,JSON.stringify(creds));
    const box=document.getElementById('urlBox');box.textContent='Bin ID (tap to copy): '+binId;box.style.display='block';
    showApp();renderAll();setSS('synced','Synced');startPoll();
  }catch(e){showErr(e.message||'Connection failed.');btn.disabled=false;btn.textContent='Connect & Sync';}
}
function copySetupUrl(){const box=document.getElementById('urlBox');const id=box.textContent.replace('Bin ID (tap to copy): ','');try{navigator.clipboard.writeText(id);box.textContent='Copied: '+id;}catch(e){}}
function showErr(msg){const e=document.getElementById('setupErr');e.textContent=msg;e.style.display='block';const btn=document.getElementById('connectBtn');btn.disabled=false;btn.textContent='Connect & Sync';}
function demoMode(){creds={demoMode:true};localStorage.setItem(CK,JSON.stringify(creds));loadLocal();showApp();renderAll();setSS('demo','Offline demo mode');}
function setSS(state,label){const dot=document.getElementById('sdot'),lbl=document.getElementById('slbl');if(!dot||!lbl)return;dot.className='sdot'+(state==='syncing'?' syncing':state==='synced'?' synced':state==='error'?' error':'');lbl.textContent=label;}
async function syncNow(initial){
  if(!creds||creds.demoMode)return;setSS('syncing','Syncing...');if(initial)showLoader('Loading tasks...');
  try{
    const r=await fetch('https://api.jsonbin.io/v3/b/'+creds.binId+'/latest',{headers:{'X-Master-Key':creds.apiKey}});
    if(!r.ok)throw new Error('HTTP '+r.status);const j=await r.json();const d=j.record||{};
    const rt=(d.tasks)?Object.values(d.tasks):[];const rm=(d.meetings)?Object.values(d.meetings):[];const rf=(d.focusItems)?Object.values(d.focusItems):[];const rp=(d.poolTopics)?Object.values(d.poolTopics):[];const ral=Array.isArray(d.activityLog)?d.activityLog:[];
    const changed=JSON.stringify(rt)!==JSON.stringify(tasks)||JSON.stringify(rm)!==JSON.stringify(meetings)||JSON.stringify(rf)!==JSON.stringify(focusItems)||JSON.stringify(rp)!==JSON.stringify(poolTopics);
    if(changed){const was=!tasks.length;tasks=rt;meetings=rm;focusItems=rf;poolTopics=rp;activityLog=ral;saveLocal();renderAll();if(active==='report')renderReport();if(active==='agenda')renderAgendaTab();if(active==='calendar')renderCalendar();if(active==='feed')renderFeed();if(!was&&!initial)showNotif('Updated by teammate');}
    setSS('synced','Up to date · '+ago(Date.now()));
  }catch(e){setSS('error','Sync error — tap Refresh');if(initial)showNotif('Could not connect');}finally{hideLoader();}
}
async function push(){
  if(!creds||creds.demoMode){saveLocal();return;}if(saving)return;saving=true;setSS('syncing','Saving...');
  try{
    const to={},mo={},fo={},po={};tasks.forEach(t=>{to[t.id]=t;});meetings.forEach(m=>{mo[m.id]=m;});focusItems.forEach(f=>{fo[f.id]=f;});poolTopics.forEach(p=>{po[p.id]=p;});
    const r=await fetch('https://api.jsonbin.io/v3/b/'+creds.binId,{method:'PUT',headers:{'Content-Type':'application/json','X-Master-Key':creds.apiKey},body:JSON.stringify({tasks:to,meetings:mo,focusItems:fo,poolTopics:po,activityLog:activityLog.slice(-200)})});
    if(!r.ok)throw new Error('HTTP '+r.status);saveLocal();setSS('synced','Saved · '+ago(Date.now()));
  }catch(e){setSS('error','Save failed — tap Refresh');showNotif('Could not save');}finally{saving=false;}
}
function startPoll(){clearInterval(pollTimer);pollTimer=setInterval(syncNow,POLL);}
document.addEventListener('visibilitychange',()=>{if(!document.hidden&&creds&&!creds.demoMode)syncNow();});
function saveLocal(){localStorage.setItem(LK,JSON.stringify({tasks,meetings,focusItems,poolTopics,activityLog}));}
function loadLocal(){
  try{const r=JSON.parse(localStorage.getItem(LK));if(r&&Array.isArray(r.tasks)){tasks=r.tasks;meetings=r.meetings||[];focusItems=r.focusItems||[];poolTopics=r.poolTopics||[];activityLog=r.activityLog||[];}
  else{tasks=defTasks();meetings=[];focusItems=[];poolTopics=[];activityLog=[];}}catch(e){tasks=defTasks();meetings=[];focusItems=[];poolTopics=[];activityLog=[];}
}
function defTasks(){return[
  {id:uid(),name:'Job Fair Planning',cat:'Events',owner:'Pastor Andy',status:'prog',notes:'Venue confirmed',due:'',created:Date.now()-86400000*5,ts:Date.now()-86400000,comments:[],pinned:false,recurring:'none'},
  {id:uid(),name:'Resume Workshop Setup',cat:'Events',owner:'Kaitlyn',status:'not',notes:'',due:'',created:Date.now()-86400000*3,ts:Date.now()-50000000,comments:[],pinned:false,recurring:'none'},
  {id:uid(),name:'Volunteer Intake Process',cat:'Volunteer',owner:'Angie',status:'not',notes:'',due:'',created:Date.now()-86400000*2,ts:Date.now()-30000000,comments:[],pinned:false,recurring:'none'},
  {id:uid(),name:'Follow up on job board',cat:'Administrative',owner:'',status:'not',notes:'Needs owner',due:'',created:Date.now()-86400000,ts:Date.now()-10000000,comments:[],pinned:false,recurring:'none'},
];}
async function addTask(){
  const name=(document.getElementById('i-name').value||'').trim();if(!name){document.getElementById('i-name').focus();return;}
  const btn=document.getElementById('addBtn');btn.disabled=true;btn.textContent='Saving...';
  const recurring=document.getElementById('i-recurring').value||'none';
  const t={id:uid(),name,cat:document.getElementById('i-cat').value,owner:document.getElementById('i-owner').value,status:document.getElementById('i-status').value,notes:document.getElementById('i-notes').value.trim(),due:document.getElementById('i-due').value||'',created:Date.now(),ts:Date.now(),comments:[],pinned:false,recurring};
  tasks.push(t);logActivity('new-task',`New task: "${name}"`,t.owner||'Unassigned',t.id);await push();
  document.getElementById('i-name').value='';document.getElementById('i-notes').value='';document.getElementById('i-due').value='';document.getElementById('i-recurring').value='none';
  btn.disabled=false;btn.textContent='Add Task';
  const own=t.owner;if(own.includes('Andy'))go('Andy');else if(own.includes('Kaitlyn'))go('Kaitlyn');else if(own.includes('Angie'))go('Angie');else go('orphaned');
  renderAll(t.id);showNotif('Task added');
}
async function setStatus(id,status){const t=tasks.find(x=>x.id===id);if(!t||t.status===status)return;t.status=status;t.ts=Date.now();const type=status==='done'?'completed':'status-change';const msg=status==='done'?`Completed: "${t.name}"`:(`Status → ${status==='prog'?'In Progress':'Not Started'}: "${t.name}"`);logActivity(type,msg,t.owner||'Unassigned',id);renderAll();await push();showNotif('Status updated');}
async function delTask(id){if(!confirm('Remove this task?'))return;tasks=tasks.filter(t=>t.id!==id);renderAll();await push();showNotif('Task removed');}
async function assignTask(id,owner){const t=tasks.find(x=>x.id===id);if(!t)return;t.owner=owner;t.ts=Date.now();renderAll();await push();showNotif('Assigned to '+owner);}
function editNotes(id){const t=tasks.find(x=>x.id===id);if(!t)return;const d=g('nd-'+id),e=g('ne-'+id),a=g('nea-'+id);if(!d||!e||!a)return;e.value=t.notes||'';d.style.display='none';e.style.display='block';a.style.display='flex';e.focus();}
function cancelNotes(id){const d=g('nd-'+id),e=g('ne-'+id),a=g('nea-'+id);if(d)d.style.display='';if(e)e.style.display='none';if(a)a.style.display='none';}
async function saveNotes(id){const t=tasks.find(x=>x.id===id);if(!t)return;const e=g('ne-'+id);t.notes=e?e.value.trim():'';t.ts=Date.now();cancelNotes(id);const d=g('nd-'+id);if(d)d.innerHTML=t.notes?esc(t.notes):'<span style="opacity:0.45">Tap to add a note...</span>';await push();showNotif('Note saved');}
async function postComment(id){
  const inp=g('ci-'+id),asel=g('ca-'+id);const txt=(inp?inp.value:'').trim();const auth=asel?asel.value:'';
  if(!txt){if(inp)inp.focus();return;}if(!auth){if(asel)asel.style.border='1px solid var(--danger)';showNotif('Please select your name');return;}if(asel)asel.style.border='';
  const t=tasks.find(x=>x.id===id);if(!t)return;if(!t.comments)t.comments=[];
  t.comments.push({text:txt,author:auth,ts:Date.now()});t.ts=Date.now();if(inp)inp.value='';markRead(id);
  logActivity('comment',`${auth} commented on "${t.name}": "${txt.slice(0,60)}${txt.length>60?'…':''}"`,auth,id);
  refreshComments(id,t);await push();showNotif('Update posted');
}
function refreshComments(id,t){const cl=g('cl-'+id);if(!cl)return;const comments=t.comments||[];const SHOW=3,lr=readLog[id]||0;const vis=comments.length<=SHOW?comments:comments.slice(-SHOW);cl.innerHTML=vis.map(c=>{const u=c.ts>lr;return `<div class="ci${u?' u':''}"><div class="cdot"></div><div class="cbdy"><div class="ctxt">${esc(c.text)}</div><div class="cmeta">${c.author?`<span class="cauth">${esc(c.author)}</span> · `:''}${fmtDT(c.ts)}</div></div></div>`;}).join('');const sec=g('cs-'+id);if(sec){const un=unreadCnt(t);const lbl=sec.querySelector('.nl');if(lbl)lbl.innerHTML='Updates'+(comments.length?' ('+comments.length+')':'')+(un>0?` <span class="ubadge">${un} new</span>`:'');const card=sec.closest('.card');if(card)card.classList.toggle('unread',un>0);}}
function expandComments(id){const t=tasks.find(x=>x.id===id);if(!t||!t.comments)return;markRead(id);const cl=g('cl-'+id);if(!cl)return;cl.innerHTML=t.comments.map(c=>`<div class="ci"><div class="cdot"></div><div class="cbdy"><div class="ctxt">${esc(c.text)}</div><div class="cmeta">${c.author?`<span class="cauth">${esc(c.author)}</span> · `:''}${fmtDT(c.ts)}</div></div></div>`).join('');const btn=cl.previousElementSibling;if(btn&&btn.classList.contains('exbtn'))btn.remove();refreshComments(id,t);}
function renderAll(newId){updateCounts();renderFocus();renderView(newId);}
function updateCounts(){
  PEOPLE.forEach(p=>{const n=tasks.filter(t=>t.status!=='done'&&p.match(t)).length;const el=g('tc-'+p.key);if(el){el.textContent=n;el.className='tc'+(n>0?' w':'');}});
  CATS.forEach(c=>{const n=tasks.filter(t=>t.status!=='done'&&t.cat===c.key).length;const el=g('tc-'+c.key);if(el){el.textContent=n;el.className='tc'+(n>0?' w':'');}});
  const orph=tasks.filter(t=>t.status!=='done'&&!t.owner);const oel=g('tc-orphaned');if(oel){oel.textContent=orph.length;oel.className='tc'+(orph.length>0?' d':'');}
  const pend=meetings.reduce((n,m)=>n+(m.agendaItems||[]).filter(a=>!a.discussed).length,0);const ael=g('tc-agenda');if(ael){ael.textContent=pend;ael.className='tc'+(pend>0?' a':'');}
  const tot=tasks.length,dn=tasks.filter(t=>t.status==='done').length;const hs=g('hdrStat');if(hs)hs.textContent=tot+' task'+(tot!==1?'s':'')+' · '+dn+' complete';
}
function renderView(newId){
  const tab=active;if(['add','report','agenda','meetings','calendar','feed'].includes(tab))return;
  const isPerson=PEOPLE.some(p=>p.key===tab);
  const sw=g('search-wrap'),fb=g('filterBar');
  if(sw)sw.style.display=tab==='orphaned'||isPerson||CATS.some(c=>c.key===tab)?'':'none';
  if(fb)fb.style.display=isPerson?'':'none';
  let allFiltered=[],hhtml='',sections=[];
  if(tab==='orphaned'){
    allFiltered=tasks.filter(t=>!t.owner||!t.owner.trim());
    hhtml='<div class="obanner">These tasks have no owner. Tap a card to assign.</div>';
    CATS.forEach(c=>{const ct=applySearch(allFiltered.filter(t=>t.cat===c.key));if(ct.length)sections.push({label:c.label,col:c.col,tasks:ct});});
  }else{
    const p=PEOPLE.find(x=>x.key===tab);const c=CATS.find(x=>x.key===tab);
    if(p){
      allFiltered=tasks.filter(t=>p.match(t));
      const overdue=allFiltered.filter(t=>t.status!=='done'&&t.due&&new Date(t.due+'T00:00:00')<new Date().setHours(0,0,0,0));
      hhtml=`<div class="vh"><div class="vav" style="background:${p.bg};color:${p.col}">${p.ini}</div><div><div class="vt">${p.label}</div><div class="vs">${allFiltered.length} task${allFiltered.length!==1?'s':''}</div></div></div>`;
      if(overdue.length&&filterMode==='all'&&!searchQuery){const today=new Date();today.setHours(0,0,0,0);hhtml+=`<div class="overdue-banner-wrap"><div class="overdue-banner-hdr">🔴 Overdue (${overdue.length})</div>${overdue.map(t=>{const days=Math.round((today-new Date(t.due+'T00:00:00'))/86400000);return `<div class="overdue-row" onclick="scrollToTask('${t.id}')"><span class="overdue-row-name">${esc(t.name)}</span><span class="overdue-days">${days}d overdue</span></div>`;}).join('')}</div>`;}
      let filtered=applyFilter(applySearch(allFiltered));filtered=[...filtered].sort((a,b)=>{if(a.pinned&&!b.pinned)return -1;if(!a.pinned&&b.pinned)return 1;return (b.created||b.ts)-(a.created||a.ts);});
      CATS.forEach(cx=>{const ct=filtered.filter(t=>t.cat===cx.key);if(ct.length)sections.push({label:cx.label,col:cx.col,tasks:ct});});
    }else if(c){
      allFiltered=tasks.filter(t=>t.cat===tab);hhtml=`<div class="vh"><div class="vt">${c.label}</div></div>`;
      let filtered=applySearch(allFiltered).sort((a,b)=>(b.created||b.ts)-(a.created||a.ts));
      const owners=[...new Set(filtered.map(t=>t.owner||'Unassigned'))];owners.forEach(o=>{const ct=filtered.filter(t=>(t.owner||'Unassigned')===o);if(ct.length)sections.push({label:o,col:o==='Unassigned'?'var(--danger)':'var(--muted)',tasks:ct});});
    }
  }
  const baseFiltered=tab==='orphaned'?tasks.filter(t=>!t.owner||!t.owner.trim()):(PEOPLE.find(x=>x.key===tab)?tasks.filter(t=>PEOPLE.find(x=>x.key===tab).match(t)):tasks.filter(t=>t.cat===tab));
  const ct=g('c-todo'),cp=g('c-prog'),cd=g('c-done');
  if(ct)ct.textContent=baseFiltered.filter(t=>t.status==='not').length;if(cp)cp.textContent=baseFiltered.filter(t=>t.status==='prog').length;if(cd)cd.textContent=baseFiltered.filter(t=>t.status==='done').length;
  const ha=g('vh-area');if(ha)ha.innerHTML=hhtml;const sv=g('vsections');if(sv)sv.innerHTML='';const ev=g('vempty');
  const totalVisible=sections.reduce((n,s)=>n+s.tasks.length,0);if(!totalVisible){if(ev)ev.style.display='';return;}if(ev)ev.style.display='none';
  sections.forEach(sec=>{const w=document.createElement('div');const lbl=document.createElement('div');lbl.className='slbl2';lbl.style.color=sec.col;lbl.textContent=sec.label;w.appendChild(lbl);sec.tasks.forEach(t=>w.appendChild(buildCard(t,newId,isPerson)));if(sv)sv.appendChild(w);});
}
function applySearch(arr){if(!searchQuery)return arr;const q=searchQuery.toLowerCase();return arr.filter(t=>t.name.toLowerCase().includes(q)||(t.notes&&t.notes.toLowerCase().includes(q))||(t.owner&&t.owner.toLowerCase().includes(q)));}
function applyFilter(arr){const today=new Date();today.setHours(0,0,0,0);if(filterMode==='quickwins')return arr.filter(t=>t.status==='not'&&(!t.due||new Date(t.due+'T00:00:00')>new Date(today.getTime()+3*86400000)));if(filterMode==='pinned')return arr.filter(t=>t.pinned);if(filterMode==='overdue')return arr.filter(t=>t.status!=='done'&&t.due&&new Date(t.due+'T00:00:00')<today);return arr;}
function setFilter(mode){filterMode=mode;['all','quickwins','pinned','overdue'].forEach(m=>{const btn=g('fb-'+m);if(!btn)return;btn.classList.remove('active','warn-active','sun-active');if(m===mode){if(m==='overdue')btn.classList.add('warn-active');else if(m==='quickwins')btn.classList.add('sun-active');else btn.classList.add('active');}});renderView();}
function onSearch(val){searchQuery=val.trim();const sc=g('searchClear');if(sc)sc.style.display=val?'':'none';renderView();}
function clearSearch(){searchQuery='';const si=g('searchInput');if(si)si.value='';const sc=g('searchClear');if(sc)sc.style.display='none';renderView();}
function scrollToTask(id){const w=document.getElementById('card-wrap-'+id);if(w){w.classList.add('open');setTimeout(()=>w.scrollIntoView({behavior:'smooth',block:'center'}),100);}}
function toggleBatch(){batchMode=!batchMode;batchSelected.clear();const bar=g('batchBar');if(bar)bar.classList.toggle('show',batchMode);const btn=g('fb-batch');if(btn)btn.classList.toggle('active',batchMode);updateBatchLabel();renderView();}
function toggleBatchSelect(id){if(batchSelected.has(id))batchSelected.delete(id);else batchSelected.add(id);updateBatchLabel();const cb=document.getElementById('cb-'+id);if(cb){cb.classList.toggle('checked',batchSelected.has(id));cb.textContent=batchSelected.has(id)?'✓'='';}}
function updateBatchLabel(){const lbl=g('batchLabel');if(lbl)lbl.textContent=batchSelected.size+' selected';}
async function batchComplete(){if(!batchSelected.size){showNotif('Select some tasks first');return;}const count=batchSelected.size;batchSelected.forEach(id=>{const t=tasks.find(x=>x.id===id);if(t&&t.status!=='done'){t.status='done';t.ts=Date.now();logActivity('completed',`Batch completed: "${t.name}"`,t.owner||'Unassigned',id);}});toggleBatch();renderAll();await push();showNotif(count+' task'+(count!==1?'s':'')+' marked complete');}
async function togglePin(id){const t=tasks.find(x=>x.id===id);if(!t)return;t.pinned=!t.pinned;t.ts=Date.now();if(t.pinned)logActivity('pinned',`Pinned: "${t.name}"`,t.owner||'Unassigned',id);renderAll();await push();showNotif(t.pinned?'Task pinned to top':'Task unpinned');}
function logActivity(type,text,who,taskId){activityLog.push({id:uid(),type,text,who:who||'',taskId:taskId||'',ts:Date.now()});if(activityLog.length>200)activityLog=activityLog.slice(-200);}
function renderFeed(){const list=g('feedList');if(!list)return;if(!activityLog.length){list.innerHTML='<div class="feed-empty">No activity yet — start adding tasks!</div>';return;}const sorted=[...activityLog].sort((a,b)=>b.ts-a.ts);list.innerHTML=sorted.map(item=>`<div class="feed-item"><div class="feed-dot ${item.type}"></div><div class="feed-body"><div class="feed-text">${esc(item.text)}</div><div class="feed-meta">${item.who?esc(item.who)+' · ':''}${fmtDT(item.ts)}</div></div></div>`).join('');}
function checkRecurring(){const today=new Date();today.setHours(0,0,0,0);let added=0;tasks.filter(t=>t.status==='done'&&t.recurring&&t.recurring!=='none').forEach(t=>{const days=t.recurring==='weekly'?7:30;const completedAgo=Math.floor((Date.now()-t.ts)/86400000);if(completedAgo>=days){const newTask={...t,id:uid(),status:'not',created:Date.now(),ts:Date.now(),comments:[],pinned:false};if(t.due){const d=new Date(t.due+'T00:00:00');d.setDate(d.getDate()+days);newTask.due=d.toISOString().split('T')[0];}tasks.push(newTask);logActivity('new-task',`Recurring task renewed: "${t.name}"`,t.owner||'Unassigned',newTask.id);added++;}});if(added>0){push();renderAll();showNotif(added+' recurring task'+(added!==1?'s':'')+' renewed!');}}
function toggleDark(){const isDark=document.documentElement.getAttribute('data-theme')==='dark';document.documentElement.setAttribute('data-theme',isDark?'light':'dark');localStorage.setItem('ccfwb_dark',isDark?'0':'1');const btn=g('darkBtn');if(btn)btn.textContent=isDark?'🌙':'☀️';}
function buildCard(t,newId,compact){
  const cat=CATS.find(c=>c.key===t.cat)||{label:t.cat};const isOrph=!t.owner||!t.owner.trim();
  const cTs=t.created||t.ts;const ageDays=Math.floor((Date.now()-cTs)/86400000);
  let ac='age',al='';if(ageDays===0)al='Created today';else if(ageDays===1)al='1 day old';else al=ageDays+' days old';if(ageDays>=14)ac='age stale';else if(ageDays>=7)ac='age old';
  const ageChip=`<span class="dc ${ac}">⏱ ${al}</span>`;
  let dueChip='',dueCompact='';
  if(t.due){const dd=new Date(t.due+'T00:00:00'),today=new Date();today.setHours(0,0,0,0);const diff=Math.round((dd-today)/86400000);const fmtD=dd.toLocaleDateString('en-US',{month:'short',day:'numeric'});if(t.status!=='done'){let dc='due',dl='',ds='';if(diff<0){dc='overdue';dl='Overdue by '+Math.abs(diff)+'d';ds='🔴';}else if(diff===0){dc='today';dl='Due today';ds='📅';}else if(diff<=3){dc='soon';dl='Due '+fmtD;ds='⚠️';}else{dc='due';dl='Due '+fmtD;ds='📅';}dueChip=`<span class="dc ${dc}">📅 ${dl}</span>`;dueCompact=`<span class="dc ${dc}" style="font-size:11px;padding:2px 7px">${ds} ${diff<0?Math.abs(diff)+'d late':diff===0?'Today':fmtD}</span>`;}else{dueChip=`<span class="dc due" style="opacity:0.5">📅 ${fmtD}</span>`;dueCompact=`<span class="dc due" style="font-size:11px;padding:2px 7px;opacity:0.5">📅 ${fmtD}</span>`;}}
  const owHtml=isOrph?'<span style="font-size:12px;color:var(--danger);background:var(--dl);padding:3px 9px;border-radius:20px;font-weight:600">Unassigned</span>':`<span class="ow"><span class="owdot">${ini(t.owner)}</span>${esc(t.owner)}</span>`;
  const assignHtml=isOrph?`<div style="margin-top:11px;display:flex;gap:7px;flex-wrap:wrap"><span style="font-size:12px;color:var(--muted);padding-top:6px">Assign:</span><button onclick="assignTask('${t.id}','Pastor Andy')" style="font-size:12px;padding:5px 12px;border-radius:20px;border:1px solid var(--border);background:var(--anb);color:var(--anc);cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600">Pastor Andy</button><button onclick="assignTask('${t.id}','Kaitlyn')" style="font-size:12px;padding:5px 12px;border-radius:20px;border:1px solid var(--border);background:var(--kab);color:var(--kac);cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600">Kaitlyn</button><button onclick="assignTask('${t.id}','Angie')" style="font-size:12px;padding:5px 12px;border-radius:20px;border:1px solid var(--border);background:var(--agb);color:var(--agc);cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600">Angie</button></div>`:'';
  const comments=t.comments||[];const SHOW=3,lr=readLog[t.id]||0,un=unreadCnt(t);const vis=comments.length<=SHOW?comments:comments.slice(-SHOW);const hid=comments.length-SHOW;
  const cHtml=vis.map(c=>{const u=c.ts>lr;return `<div class="ci${u?' u':''}"><div class="cdot"></div><div class="cbdy"><div class="ctxt">${esc(c.text)}</div><div class="cmeta">${c.author?`<span class="cauth">${esc(c.author)}</span> · `:''}${fmtDT(c.ts)}</div></div></div>`;}).join('');
  const bodyHtml=`<div class="cm"><span class="cb cb-${t.cat}">${cat.label}</span>${owHtml}<span class="ts">${ago(t.ts)}</span></div><div class="dr">${ageChip}${dueChip}</div><div class="stog"><button class="sbtn ${t.status==='not'?'not':''}" onclick="setStatus('${t.id}','not')">Not Started</button><button class="sbtn ${t.status==='prog'?'prog':''}" onclick="setStatus('${t.id}','prog')">In Progress</button><button class="sbtn ${t.status==='done'?'done':''}" onclick="setStatus('${t.id}','done')">Complete</button></div>${assignHtml}<div class="ns"><div class="nl">Notes</div><div class="nd" id="nd-${t.id}" onclick="editNotes('${t.id}')">${t.notes?esc(t.notes):'<span style="opacity:0.45">Tap to add a note...</span>'}</div><textarea class="ne" id="ne-${t.id}" placeholder="Add a note..."></textarea><div class="nea" id="nea-${t.id}"><button class="nsave" onclick="saveNotes('${t.id}')">Save</button><button class="ncanc" onclick="cancelNotes('${t.id}')">Cancel</button></div></div><div class="cs" id="cs-${t.id}"><div class="nl">Updates${comments.length?' ('+comments.length+')':''}${un>0?` <span class="ubadge">${un} new</span>`:''}</div>${comments.length>SHOW?`<button class="exbtn" onclick="expandComments('${t.id}')">Show ${hid} earlier update${hid!==1?'s':''}</button>`:''}<div id="cl-${t.id}">${cHtml}</div><div class="ciw"><div class="car"><span class="cal">From:</span><select class="cas" id="ca-${t.id}"><option value="">— Select your name —</option><option value="Pastor Andy">Pastor Andy</option><option value="Kaitlyn">Kaitlyn</option><option value="Angie">Angie</option></select></div><div class="cir"><textarea class="cin" id="ci-${t.id}" placeholder="Type an update..." rows="2" onkeydown="if(event.key==='Enter'&&!event.shiftKey){event.preventDefault();postComment('${t.id}')}"></textarea><button class="csub" onclick="postComment('${t.id}')">Post</button></div></div></div>`;
  if(compact){
    const d=document.createElement('div');d.className='card-compact'+(t.id===newId?' open flash':'')+(un>0?' unread':'');d.id='card-wrap-'+t.id;
    const statusBar=`<div class="card-status-bar ${t.status}"></div>`;const unreadPip=un>0?`<span class="ubadge" style="font-size:10px">${un}</span>`:'';
    const pinBtn=`<button class="pin-btn${t.pinned?' pinned':''}" onclick="event.stopPropagation();togglePin('${t.id}')" title="${t.pinned?'Unpin':'Pin to top'}">${t.pinned?'📌':'📍'}</button>`;
    const recBadge=t.recurring&&t.recurring!=='none'?`<span class="rec-badge">🔄 ${t.recurring}</span>`:'';
    const checkbox=`<div class="card-checkbox${batchMode?' show':''}${batchSelected.has(t.id)?' checked':''}" id="cb-${t.id}" onclick="event.stopPropagation();toggleBatchSelect('${t.id}')">${batchSelected.has(t.id)?'✓':''}</div>`;
    d.innerHTML=`<div class="card-compact-row" onclick="${batchMode?`toggleBatchSelect('${t.id}')`:`toggleCard('${t.id}')`}">${checkbox}${statusBar}<div class="card-compact-name${t.status==='done'?' done-text':''}">${esc(t.name)}${recBadge?` ${recBadge}`:''}</div><div class="card-compact-meta">${dueCompact}${unreadPip}<span class="cb cb-${t.cat}" style="font-size:11px;padding:2px 7px">${cat.label}</span>${pinBtn}<button class="delbtn" style="font-size:17px;padding:0 2px" onclick="event.stopPropagation();delTask('${t.id}')">×</button><span class="card-compact-chevron">›</span></div></div><div class="card-body"><div class="card-body-inner"><div style="font-weight:600;font-size:16px;margin-bottom:10px">${esc(t.name)}</div>${bodyHtml}</div></div>`;
    return d;
  }
  const d=document.createElement('div');d.className='card'+(t.id===newId?' flash':'')+(un>0?' unread':'');d.innerHTML=`<div class="ct"><div class="cn">${esc(t.name)}</div><button class="delbtn" onclick="delTask('${t.id}')">×</button></div>${bodyHtml}`;return d;
}
function toggleCard(id){const wrap=document.getElementById('card-wrap-'+id);if(!wrap)return;const wasOpen=wrap.classList.contains('open');wrap.classList.toggle('open',!wasOpen);if(!wasOpen){markRead(id);const t=tasks.find(x=>x.id===id);if(t)refreshComments(id,t);}}
function renderFocus(){
  const area=g('focus-area');if(!area)return;if(['add','report','agenda','meetings','calendar','feed'].includes(active)){area.innerHTML='';return;}
  const items=focusItems||[];const sorted=[...items].sort((a,b)=>{if(a.done!==b.done)return a.done?1:-1;return b.ts-a.ts;});
  let itemsHtml='';if(!sorted.length){itemsHtml='<div class="focus-empty">No priorities yet. Tap + Add to set this week\'s focus.</div>';}else{itemsHtml=sorted.map(i=>`<div class="focus-item${i.done?' done':''}"><div class="focus-chk${i.done?' on':''}" onclick="toggleFocus('${i.id}')">${i.done?'✓':''}</div><div style="flex:1"><div class="focus-text">${esc(i.text)}</div><div class="focus-meta">${i.author?esc(i.author)+' · ':''}${ago(i.ts)}</div></div><button class="focus-del" onclick="deleteFocus('${i.id}')">×</button></div>`).join('');}
  area.innerHTML=`<div class="focus-banner"><div class="focus-hdr"><div><div class="focus-title">⭐ This Week's Focus</div><div class="focus-sub">Top priorities for the team</div></div><button class="focus-add-btn" onclick="showFocusForm()">+ Add</button></div><div class="focus-form" id="focus-form"><input class="focus-input" type="text" id="ff-text" placeholder="What's a priority this week?" /><select class="focus-input" id="ff-author" style="padding:8px 11px"><option value="">— Your name (optional) —</option><option value="Pastor Andy">Pastor Andy</option><option value="Kaitlyn">Kaitlyn</option><option value="Angie">Angie</option></select><div class="focus-form-row"><button class="focus-save" onclick="addFocusItem()">Add Priority</button><button class="focus-cancel" onclick="hideFocusForm()">Cancel</button></div></div><div class="focus-list">${itemsHtml}</div></div>`;
}
function showFocusForm(){const f=g('focus-form');if(f){f.classList.add('open');const t=g('ff-text');if(t)t.focus();}}
function hideFocusForm(){const f=g('focus-form');if(f)f.classList.remove('open');}
async function addFocusItem(){const text=((g('ff-text')||{}).value||'').trim();const author=(g('ff-author')||{}).value||'';if(!text){g('ff-text')?.focus();return;}focusItems.push({id:uid(),text,author,done:false,ts:Date.now()});if(g('ff-text'))g('ff-text').value='';if(g('ff-author'))g('ff-author').value='';hideFocusForm();renderFocus();await push();showNotif('Priority added');}
async function toggleFocus(id){const i=focusItems.find(x=>x.id===id);if(!i)return;i.done=!i.done;i.ts=Date.now();renderFocus();await push();}
async function deleteFocus(id){if(!confirm('Remove this priority?'))return;focusItems=focusItems.filter(i=>i.id!==id);renderFocus();await push();showNotif('Priority removed');}
function renderPool(){const list=g('pool-list'),emp=g('pool-empty');if(!list)return;const items=[...poolTopics].sort((a,b)=>b.ts-a.ts);if(!items.length){list.innerHTML='';if(emp)emp.style.display='';return;}if(emp)emp.style.display='none';list.innerHTML=items.map(p=>`<div class="pool-item"><div class="pool-body"><div class="pool-text">${esc(p.topic)}</div>${p.details?`<div class="pool-meta">${esc(p.details)}</div>`:''}<div class="pool-meta">${p.author?'Added by '+esc(p.author)+' · ':''}${ago(p.ts)}</div></div><div class="pool-actions" style="flex-direction:column;gap:5px;align-items:flex-end">${meetings.length?`<button class="pool-btn" onclick="movePoolToMeeting('${p.id}')">→ Meeting</button>`:''}<button class="pool-del" onclick="deletePoolTopic('${p.id}')">×</button></div></div>`).join('');}
function showPoolForm(){const f=g('pool-form');if(f){f.style.display='block';const t=g('pf-topic');if(t)t.focus();}}
function hidePoolForm(){const f=g('pool-form');if(f)f.style.display='none';}
async function addPoolTopic(){const topic=((g('pf-topic')||{}).value||'').trim();const details=((g('pf-details')||{}).value||'').trim();const author=(g('pf-author')||{}).value||'';if(!topic){g('pf-topic')?.focus();return;}if(!author){showNotif('Please select your name');return;}poolTopics.push({id:uid(),topic,details,author,ts:Date.now()});if(g('pf-topic'))g('pf-topic').value='';if(g('pf-details'))g('pf-details').value='';hidePoolForm();renderPool();await push();showNotif('Topic added to pool');}
async function deletePoolTopic(id){if(!confirm('Remove this topic from the pool?'))return;poolTopics=poolTopics.filter(p=>p.id!==id);renderPool();await push();showNotif('Topic removed');}
async function movePoolToMeeting(poolId){const p=poolTopics.find(x=>x.id===poolId);if(!p)return;if(!meetings.length){showNotif('Create a meeting first');return;}const sorted=[...meetings].sort((a,b)=>b.date.localeCompare(a.date));const m=sorted[0];if(!confirm(`Move "${p.topic}" to ${m.title||'Meeting'} on ${fmtDate(m.date)}?`))return;if(!m.agendaItems)m.agendaItems=[];m.agendaItems.push({topic:p.topic,details:p.details||'',author:p.author||'',discussed:false,ts:Date.now()});poolTopics=poolTopics.filter(x=>x.id!==poolId);renderPool();updateCounts();if(active==='agenda')renderAgendaItems();await push();showNotif('Topic moved to meeting');}
function renderReport(){const sL={not:'Not Started',prog:'In Progress',done:'Complete'};const sB={not:'bnot',prog:'bprog',done:'bdone'};const tot=tasks.length,dn=tasks.filter(t=>t.status==='done').length;const pg=tasks.filter(t=>t.status==='prog').length,nt=tasks.filter(t=>t.status==='not').length;const pct=tot?Math.round(dn/tot*100):0;let h=`<div class="rs"><h3>Overall Progress</h3><div style="background:var(--s2);border-radius:20px;height:7px;margin-bottom:15px;overflow:hidden"><div style="background:var(--accent);height:100%;width:${pct}%;border-radius:20px;transition:width 0.6s"></div></div><div class="rr"><span>Total tasks</span><strong>${tot}</strong></div><div class="rr"><span>Complete</span><span class="rbadge bdone">${dn}</span></div><div class="rr"><span>In Progress</span><span class="rbadge bprog">${pg}</span></div><div class="rr"><span>Not Started</span><span class="rbadge bnot">${nt}</span></div></div>`;h+=`<div class="rs"><h3>By Team Member</h3>`;PEOPLE.forEach(p=>{const pt=tasks.filter(t=>p.match(t));const pd=pt.filter(t=>t.status==='done').length;if(!pt.length){h+=`<div class="rr"><span>${p.label}</span><span style="font-size:13px;color:var(--muted)">No tasks</span></div>`;return;}h+=`<div class="mblk"><div class="mhdr"><div class="mavs" style="background:${p.bg};color:${p.col}">${p.ini}</div><span class="mname">${p.label}</span><span class="mcnt">${pt.length} task${pt.length!==1?'s':''} · ${pd} done</span></div>`;pt.forEach(t=>{h+=`<div class="rr" style="padding-left:38px"><span style="font-size:14px">${esc(t.name)}</span><span class="rbadge ${sB[t.status]}">${sL[t.status]}</span></div>`;});h+=`</div>`;});h+=`</div>`;h+=`<div class="rs"><h3>By Category</h3>`;CATS.forEach(c=>{const ct=tasks.filter(t=>t.cat===c.key);if(!ct.length)return;const cd=ct.filter(t=>t.status==='done').length;h+=`<div class="rr"><span>${c.label}</span><span style="font-size:13px;color:var(--muted)">${cd}/${ct.length} done</span></div>`;});h+=`</div>`;const today=new Date();today.setHours(0,0,0,0);const ov=tasks.filter(t=>t.due&&t.status!=='done'&&new Date(t.due+'T00:00:00')<today);if(ov.length){h+=`<div class="rs"><h3 style="color:var(--danger)">Overdue (${ov.length})</h3>`;ov.forEach(t=>{const dy=Math.round((today-new Date(t.due+'T00:00:00'))/86400000);h+=`<div class="rr"><span style="font-size:14px">${esc(t.name)} <span style="font-size:12px;color:var(--muted)">${t.owner||'Unassigned'}</span></span><span style="font-size:12px;color:var(--danger);font-weight:600">${dy}d overdue</span></div>`;});h+=`</div>`;}const orph=tasks.filter(t=>!t.owner||!t.owner.trim());if(orph.length){h+=`<div class="rs"><h3 style="color:var(--danger)">Orphaned (${orph.length})</h3>`;orph.forEach(t=>{h+=`<div class="rr"><span style="font-size:14px">${esc(t.name)}</span><span class="rbadge ${sB[t.status]}">${sL[t.status]}</span></div>`;});h+=`</div>`;}const now=new Date();h+=`<div style="text-align:center;font-size:12px;color:var(--muted);padding:9px 0 5px">Generated ${now.toLocaleDateString()} at ${now.toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'})}</div>`;const rc=g('report-content');if(rc)rc.innerHTML=h;}
function fmtDate(s){if(!s)return'';const d=new Date(s+'T00:00:00');return d.toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric',year:'numeric'});}
function renderAgendaTab(){const sel=g('agenda-sel');if(!sel)return;const prev=sel.value;sel.innerHTML='<option value="">— Select a meeting —</option>';[...meetings].sort((a,b)=>b.date.localeCompare(a.date)).forEach(m=>{const o=document.createElement('option');o.value=m.id;o.textContent=(m.title||'Meeting')+' · '+fmtDate(m.date);sel.appendChild(o);});if(prev)sel.value=prev;renderPool();renderAgendaItems();}
function renderAgendaItems(){const sel=g('agenda-sel');const mid=sel?sel.value:'';const panel=g('agenda-panel');if(!mid){if(panel)panel.style.display='none';return;}if(panel)panel.style.display='';const m=meetings.find(x=>x.id===mid);if(!m)return;const te=g('agenda-title'),de=g('agenda-date');if(te)te.textContent=m.title||'Meeting';if(de)de.textContent=fmtDate(m.date);const list=g('agenda-list'),emp=g('agenda-empty');const items=m.agendaItems||[];if(!items.length){if(list)list.innerHTML='';if(emp)emp.style.display='';return;}if(emp)emp.style.display='none';if(list)list.innerHTML=items.map((a,i)=>`<div class="ai${a.discussed?' done':''}"><div class="aichk${a.discussed?' on':''}" onclick="toggleItem('${m.id}',${i})">${a.discussed?'✓':''}</div><div class="aibdy"><div class="ait">${esc(a.topic)}</div>${a.details?`<div class="aidet">${esc(a.details)}</div>`:''}<div class="aimeta">${a.author?'Added by '+esc(a.author)+' · ':''}${ago(a.ts)}</div></div></div>`).join('');}
function showMtgForm(ctx){const f=g('mtg-form-'+ctx);if(!f)return;f.style.display='block';const d=g('mf-date-'+ctx),t=g('mf-title-'+ctx);if(d)d.value='';if(t)t.value='';}
function hideMtgForm(ctx){const f=g('mtg-form-'+ctx);if(f)f.style.display='none';}
async function createMeeting(ctx){const date=(g('mf-date-'+ctx)||{}).value||'';const title=((g('mf-title-'+ctx)||{}).value||'').trim()||'Team Meeting';if(!date){showNotif('Please pick a date');return;}const m={id:uid(),date,title,notes:'',attachments:[],agendaItems:[],ts:Date.now()};meetings.push(m);hideMtgForm(ctx);await push();updateCounts();if(ctx==='meetings'){renderMeetingsTab();}else{renderAgendaTab();const sel=g('agenda-sel');if(sel){sel.value=m.id;renderAgendaItems();}}showNotif('Meeting created');}
function showTopicForm(){const f=g('topic-form');if(f)f.style.display='block';}
function hideTopicForm(){const f=g('topic-form');if(f)f.style.display='none';}
async function addTopic(){const topic=(g('tf-topic')||{}).value?.trim()||'';const author=(g('tf-author')||{}).value||'';const details=(g('tf-details')||{}).value?.trim()||'';if(!topic){g('tf-topic')?.focus();return;}if(!author){showNotif('Please select your name');return;}const sel=g('agenda-sel');const mid=sel?sel.value:'';const m=meetings.find(x=>x.id===mid);if(!m)return;if(!m.agendaItems)m.agendaItems=[];m.agendaItems.push({topic,details,author,discussed:false,ts:Date.now()});if(g('tf-topic'))g('tf-topic').value='';if(g('tf-details'))g('tf-details').value='';hideTopicForm();await push();updateCounts();renderAgendaItems();showNotif('Topic added');}
async function toggleItem(mid,idx){const m=meetings.find(x=>x.id===mid);if(!m||!m.agendaItems[idx])return;m.agendaItems[idx].discussed=!m.agendaItems[idx].discussed;await push();updateCounts();renderAgendaItems();}
function renderMeetingsTab(){const listEl=g('mtg-list'),empEl=g('mtg-empty');const sorted=[...meetings].sort((a,b)=>b.date.localeCompare(a.date));if(!sorted.length){if(listEl)listEl.innerHTML='';if(empEl)empEl.style.display='';return;}if(empEl)empEl.style.display='none';if(listEl)listEl.innerHTML=sorted.map(m=>`<div class="mrow" onclick="openMtg('${m.id}')"><div><div class="mrow-t">${esc(m.title||'Meeting')}</div><div class="mrow-m">${fmtDate(m.date)}${m.attachments&&m.attachments.length?' · '+m.attachments.length+' attachment'+(m.attachments.length!==1?'s':''):''}</div></div><span style="color:var(--muted);font-size:20px">›</span></div>`).join('');}
function openMtg(mid){activeMtg=mid;const m=meetings.find(x=>x.id===mid);if(!m)return;if(active!=='meetings'){active='meetings';ALL_TABS.forEach(k=>{const btn=g('tb-'+k);if(btn)btn.classList.toggle('on',k===active);});const pv=g('pv-view'),pa=g('pv-add'),pr=g('pv-report'),pg=g('pv-agenda'),pm=g('pv-meetings'),pc=g('pv-calendar'),pf=g('pv-feed');if(pv)pv.style.display='none';if(pa)pa.style.display='none';if(pr)pr.style.display='none';if(pg)pg.style.display='none';if(pc)pc.style.display='none';if(pf)pf.style.display='none';if(pm)pm.style.display='';}const lv=g('mtg-list-view'),dv=g('mtg-detail-view');if(lv)lv.style.display='none';if(dv)dv.style.display='';const te=g('dtl-title'),de=g('dtl-date'),ne=g('dtl-notes');if(te)te.textContent=m.title||'Meeting';if(de)de.textContent=fmtDate(m.date);if(ne)ne.value=m.notes||'';renderAtts(m);const needsSetup=!creds||!creds.cloudName||!creds.cloudPreset;const banner=g('cl-banner');if(banner)banner.style.display=needsSetup?'':'none';}
function closeMtgDetail(){activeMtg=null;const lv=g('mtg-list-view'),dv=g('mtg-detail-view');if(lv)lv.style.display='';if(dv)dv.style.display='none';}
async function saveMtgNotes(){const m=meetings.find(x=>x.id===activeMtg);if(!m)return;const el=g('dtl-notes');m.notes=el?el.value:'';await push();showNotif('Notes saved');}
function renderAtts(m){const list=g('dtl-atts');if(!list)return;list.innerHTML=(m.attachments||[]).map(a=>`<a class="attchip" href="${a.url}" target="_blank">📄 ${esc(a.name)}</a>`).join('');}
async function uploadFile(event){const file=event.target.files[0];if(!file)return;if(!creds||!creds.cloudName||!creds.cloudPreset){showNotif('Set up Cloudinary in ⚙ Settings first');const b=g('cl-banner');if(b)b.style.display='';return;}const prog=g('up-prog');if(prog){prog.style.display='';prog.textContent='Uploading '+file.name+'...';}try{const fd=new FormData();fd.append('file',file);fd.append('upload_preset',creds.cloudPreset);const r=await fetch('https://api.cloudinary.com/v1_1/'+creds.cloudName+'/auto/upload',{method:'POST',body:fd});if(!r.ok)throw new Error('Upload failed');const data=await r.json();const m=meetings.find(x=>x.id===activeMtg);if(!m)return;if(!m.attachments)m.attachments=[];m.attachments.push({name:file.name,url:data.secure_url,ts:Date.now()});renderAtts(m);await push();showNotif('File uploaded');}catch(e){showNotif('Upload failed — check Cloudinary settings');}finally{if(prog)prog.style.display='none';event.target.value='';}}
function setMode(mode){const sp=g('single-panel'),bp=g('bulk-panel');const ms=g('mb-single'),mb=g('mb-bulk');if(sp)sp.style.display=mode==='single'?'':'none';if(bp)bp.style.display=mode==='bulk'?'':'none';if(ms)ms.classList.toggle('on',mode==='single');if(mb)mb.classList.toggle('on',mode==='bulk');if(mode==='bulk')backToPaste();}
function parseBulk(){const raw=(g('bulk-input')||{}).value||'';const lines=raw.split('\n').map(l=>l.trim()).filter(l=>l.length>0);if(!lines.length){showNotif('Please paste at least one task');return;}const tb=g('btbody');if(tb)tb.innerHTML=lines.map((line,i)=>`<tr id="br-${i}"><td><input class="btn-name" type="text" value="${esc(line)}" id="bn-${i}" /></td><td><select class="bsel" id="bo-${i}"><option value="">Unassigned</option><option value="Pastor Andy">Pastor Andy</option><option value="Kaitlyn">Kaitlyn</option><option value="Angie">Angie</option></select></td><td><select class="bsel" id="bc-${i}"><option value="Events">Events</option><option value="Projects">Projects</option><option value="Administrative">Admin</option><option value="Volunteer">Volunteer</option></select></td><td><button class="brem" onclick="remBulkRow(${i})">×</button></td></tr>`).join('');const bc=g('bcount');if(bc)bc.textContent=lines.length+' task'+(lines.length!==1?'s':'')+' — set owner and category:';const pp=g('bulk-paste'),pr=g('bulk-review');if(pp)pp.style.display='none';if(pr)pr.style.display='';}
function remBulkRow(i){const row=g('br-'+i);if(row)row.remove();const rem=document.querySelectorAll('#btbody tr').length;const bc=g('bcount');if(bc)bc.textContent=rem+' task'+(rem!==1?'s':'')+' ready:';if(!rem)backToPaste();}
function backToPaste(){const pp=g('bulk-paste'),pr=g('bulk-review');if(pp)pp.style.display='';if(pr)pr.style.display='none';}
async function saveBulk(){const rows=document.querySelectorAll('#btbody tr');if(!rows.length){showNotif('No tasks to save');return;}const btn=g('bulkSaveBtn');if(btn){btn.disabled=true;btn.textContent='Saving...';}let count=0;rows.forEach(row=>{const i=row.id.replace('br-','');const name=((g('bn-'+i)||{}).value||'').trim();if(!name)return;tasks.push({id:uid(),name,cat:(g('bc-'+i)||{}).value||'Administrative',owner:(g('bo-'+i)||{}).value||'',status:'not',notes:'',due:'',created:Date.now(),ts:Date.now(),comments:[],pinned:false,recurring:'none'});count++;});await push();renderAll();if(btn){btn.disabled=false;btn.textContent='Save All Tasks';}const pi=g('bulk-input');if(pi)pi.value='';backToPaste();setMode('single');go('Andy');showNotif(count+' task'+(count!==1?'s':'')+' added!');}
function pad(n){return String(n).padStart(2,'0');}
function tickClock(){const now=new Date();let h=now.getHours();const m=now.getMinutes(),s=now.getSeconds();const meridiem=h>=12?'PM':'AM';h=h%12||12;const hc=g('hdrClock');if(hc)hc.textContent=`${h}:${pad(m)} ${meridiem}`;const bc=g('bigClockTime');if(bc)bc.innerHTML=`${h}:${pad(m)}<span class="cal-clock-sec">${pad(s)}</span><span class="cal-clock-mer">${meridiem}</span>`;const bd=g('bigClockDate'),bday=g('bigClockDay');if(bd||bday){const days=['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];const months=['January','February','March','April','May','June','July','August','September','October','November','December'];if(bday)bday.textContent=days[now.getDay()];if(bd)bd.textContent=`${months[now.getMonth()]} ${now.getDate()}, ${now.getFullYear()}`;}}
function renderCalendar(){const monthNames=['January','February','March','April','May','June','July','August','September','October','November','December'];const title=g('calMonthTitle');if(title)title.innerHTML=`${monthNames[calViewMonth]} <em>${calViewYear}</em>`;const firstDay=new Date(calViewYear,calViewMonth,1).getDay();const daysInMonth=new Date(calViewYear,calViewMonth+1,0).getDate();const today=new Date();today.setHours(0,0,0,0);const todayStr=`${today.getFullYear()}-${pad(today.getMonth()+1)}-${pad(today.getDate())}`;const dateMap={};tasks.forEach(t=>{if(t.due){if(!dateMap[t.due])dateMap[t.due]={tasks:[],meetings:[]};dateMap[t.due].tasks.push(t);}});meetings.forEach(m=>{if(m.date){if(!dateMap[m.date])dateMap[m.date]={tasks:[],meetings:[]};dateMap[m.date].meetings.push(m);}});const grid=g('calGrid');if(!grid)return;let html='';for(let i=0;i<firstDay;i++){html+='<div class="cal-day empty"></div>';}for(let d=1;d<=daysInMonth;d++){const dateStr=`${calViewYear}-${pad(calViewMonth+1)}-${pad(d)}`;const isToday=dateStr===todayStr;const isSelected=dateStr===calSelected;const info=dateMap[dateStr];let dots='';if(info){const cellDate=new Date(dateStr+'T00:00:00');const overdue=info.tasks.filter(t=>t.status!=='done'&&cellDate<today).length;const pendingTasks=info.tasks.filter(t=>t.status!=='done').length-overdue;const meetingCount=info.meetings.length;if(overdue>0)dots+='<span class="cal-dot" style="background:var(--danger)"></span>';else if(pendingTasks>0)dots+='<span class="cal-dot" style="background:var(--accent)"></span>';else if(info.tasks.length>0)dots+='<span class="cal-dot" style="background:var(--tide-dark);opacity:0.5"></span>';if(meetingCount>0)dots+='<span class="cal-dot" style="background:var(--tide)"></span>';}const cls=['cal-day'];if(isToday)cls.push('today');if(isSelected)cls.push('selected');html+=`<button class="${cls.join(' ')}" onclick="selectCalDay('${dateStr}')"><span class="cal-day-num">${d}</span><span class="cal-dots">${dots}</span></button>`;}grid.innerHTML=html;renderCalDetail();}
function calPrev(){calViewMonth--;if(calViewMonth<0){calViewMonth=11;calViewYear--;}renderCalendar();}
function calNext(){calViewMonth++;if(calViewMonth>11){calViewMonth=0;calViewYear++;}renderCalendar();}
function calToday(){const t=new Date();calViewMonth=t.getMonth();calViewYear=t.getFullYear();calSelected=`${t.getFullYear()}-${pad(t.getMonth()+1)}-${pad(t.getDate())}`;renderCalendar();}
function selectCalDay(dateStr){calSelected=(calSelected===dateStr)?null:dateStr;renderCalendar();}
function renderCalDetail(){const el=g('calDayDetail');if(!el)return;if(!calSelected){el.innerHTML='';return;}const dateObj=new Date(calSelected+'T00:00:00');const friendlyDate=dateObj.toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric',year:'numeric'});const dayTasks=tasks.filter(t=>t.due===calSelected);const dayMeetings=meetings.filter(m=>m.date===calSelected);let html=`<div class="cal-detail-card"><div class="cal-detail-title">${friendlyDate}</div>`;if(!dayTasks.length&&!dayMeetings.length){html+=`<div class="cal-detail-empty">Nothing scheduled.</div>`;}else{if(dayMeetings.length){html+=`<div class="cal-detail-section"><div class="cal-detail-label">Meetings</div>`;dayMeetings.forEach(m=>{const topicCount=(m.agendaItems||[]).length;html+=`<div class="cal-detail-item meeting" onclick="openMtg('${m.id}')"><div><div class="cal-detail-item-name">${esc(m.title||'Meeting')}</div><div class="cal-detail-item-meta">${topicCount} topic${topicCount!==1?'s':''}${m.attachments&&m.attachments.length?' · '+m.attachments.length+' attachment'+(m.attachments.length!==1?'s':''):''}</div></div><span style="color:var(--tide-dark);font-size:18px">›</span></div>`;});html+='</div>';}if(dayTasks.length){html+=`<div class="cal-detail-section"><div class="cal-detail-label">Tasks Due</div>`;dayTasks.forEach(t=>{const sB=t.status==='done'?'bdone':(t.status==='prog'?'bprog':'bnot');const sL=t.status==='done'?'Complete':(t.status==='prog'?'In Progress':'Not Started');html+=`<div class="cal-detail-item"><div><div class="cal-detail-item-name">${esc(t.name)}</div><div class="cal-detail-item-meta">${esc(t.owner||'Unassigned')} · ${esc(t.cat)}</div></div><span class="rbadge ${sB}">${sL}</span></div>`;});html+='</div>';}}html+='</div>';el.innerHTML=html;}
function go(tab){active=tab;if(!PEOPLE.some(p=>p.key===tab)){searchQuery='';filterMode='all';const si=g('searchInput');if(si)si.value='';const sc=g('searchClear');if(sc)sc.style.display='none';}ALL_TABS.forEach(k=>{const btn=g('tb-'+k);if(btn)btn.classList.toggle('on',k===tab);});const isView=!['add','report','agenda','meetings','calendar','feed'].includes(tab);const pv=g('pv-view'),pa=g('pv-add'),pr=g('pv-report'),pg=g('pv-agenda'),pm=g('pv-meetings'),pc=g('pv-calendar'),pf=g('pv-feed');if(pv)pv.style.display=isView?'':'none';if(pa)pa.style.display=tab==='add'?'':'none';if(pr)pr.style.display=tab==='report'?'':'none';if(pg)pg.style.display=tab==='agenda'?'':'none';if(pm)pm.style.display=tab==='meetings'?'':'none';if(pc)pc.style.display=tab==='calendar'?'':'none';if(pf)pf.style.display=tab==='feed'?'':'none';if(tab==='report')renderReport();else if(tab==='agenda')renderAgendaTab();else if(tab==='meetings'){renderMeetingsTab();closeMtgDetail();}else if(tab==='calendar'){renderCalendar();tickClock();}else if(tab==='feed')renderFeed();else if(isView)renderView();}
async function generateAgenda(){
  const btn=g('aiGenBtn');const out=g('ai-agenda-output');if(btn){btn.disabled=true;btn.textContent='⏳ Generating...';}if(out){out.style.display='none';out.innerHTML='';}
  const today=new Date();today.setHours(0,0,0,0);
  const overdueTasks=tasks.filter(t=>t.status!=='done'&&t.due&&new Date(t.due+'T00:00:00')<today);
  const inProgressTasks=tasks.filter(t=>t.status==='prog');const pinnedTasks=tasks.filter(t=>t.pinned&&t.status!=='done');const notStarted=tasks.filter(t=>t.status==='not');const focusList=focusItems.filter(i=>!i.done);const poolList=poolTopics;
  const weekAgo=Date.now()-7*86400000;const recentComments=[];tasks.forEach(t=>{(t.comments||[]).filter(c=>c.ts>weekAgo).forEach(c=>{recentComments.push({task:t.name,comment:c.text,author:c.author,ts:c.ts});});});
  const contextBlock=`TEAM TASK DATA — CCFWB Team (Calvary Chapel Fort Walton Beach)\nToday: ${today.toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric',year:'numeric'})}\nTeam members: Pastor Andy, Kaitlyn, Angie\n\nOVERDUE TASKS (${overdueTasks.length}):\n${overdueTasks.map(t=>`- "${t.name}" | Owner: ${t.owner||'Unassigned'} | ${Math.round((today-new Date(t.due+'T00:00:00'))/86400000)}d overdue | Cat: ${t.cat}${t.notes?' | Notes: '+t.notes:''}`).join('\n')||'None'}\n\nIN PROGRESS (${inProgressTasks.length}):\n${inProgressTasks.map(t=>`- "${t.name}" | Owner: ${t.owner||'Unassigned'} | Cat: ${t.cat}${t.notes?' | Notes: '+t.notes:''}`).join('\n')||'None'}\n\nPINNED/PRIORITY TASKS (${pinnedTasks.length}):\n${pinnedTasks.map(t=>`- "${t.name}" | Owner: ${t.owner||'Unassigned'} | Status: ${t.status}`).join('\n')||'None'}\n\nTHIS WEEK'S FOCUS ITEMS (${focusList.length}):\n${focusList.map(i=>`- ${i.text}${i.author?' ('+i.author+')':''}`).join('\n')||'None'}\n\nTOPIC POOL (${poolList.length}):\n${poolList.map(p=>`- "${p.topic}"${p.details?' — '+p.details:''}${p.author?' (added by '+p.author+')':''}`).join('\n')||'None'}\n\nNOT STARTED TASKS (${notStarted.length}):\n${notStarted.slice(0,15).map(t=>`- "${t.name}" | Owner: ${t.owner||'Unassigned'} | Cat: ${t.cat}`).join('\n')||'None'}${notStarted.length>15?`\n...and ${notStarted.length-15} more`:''}\n\nRECENT COMMENTS THIS WEEK (${recentComments.length}):\n${recentComments.slice(0,10).map(c=>`- ${c.author} on "${c.task}": "${c.comment}"`).join('\n')||'None'}`.trim();
  const prompt=`You are a ministry team assistant for a church workforce development team. Below is the current state of the team's task data.\n\n${contextBlock}\n\nGenerate a structured, ready-to-run meeting agenda for the team's next meeting. Format your response as JSON with this exact structure:\n{\n  "title": "string",\n  "duration": "string",\n  "sections": [\n    {\n      "title": "section heading",\n      "type": "urgent|focus|discussion|info|action",\n      "items": [\n        {\n          "title": "agenda item title",\n          "detail": "1-2 sentence talking point",\n          "owner": "person or empty string"\n        }\n      ]\n    }\n  ],\n  "closing_note": "string"\n}\nPrioritize: overdue first, then pinned/focus, then in-progress, then topic pool. Keep it practical. Respond with valid JSON only, no markdown.`;
  try{
    const response=await fetch('https://api.anthropic.com/v1/messages',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:1000,messages:[{role:'user',content:prompt}]})});
    const data=await response.json();const raw=data.content?.find(b=>b.type==='text')?.text||'';
    let agenda;try{agenda=JSON.parse(raw.replace(/```json|```/g,'').trim());}catch(e){if(out){out.style.display='';out.innerHTML=`<div class="ai-agenda-output"><h3>🤖 Generated Agenda</h3><div class="ai-agenda-raw">${esc(raw)}</div></div>`;}return;}
    const typeColors={urgent:'urgent',focus:'focus',discussion:'',info:'info',action:''};
    let html=`<div class="ai-agenda-output"><h3>🤖 ${esc(agenda.title||'Meeting Agenda')}</h3><div style="font-size:13px;color:var(--muted);margin-bottom:16px">Estimated time: ${esc(agenda.duration||'—')}</div>`;
    (agenda.sections||[]).forEach(sec=>{html+=`<div class="ai-agenda-section"><div class="ai-agenda-section-title">${esc(sec.title||'')}</div>`;(sec.items||[]).forEach(item=>{const cls=typeColors[sec.type]||'';html+=`<div class="ai-agenda-item${cls?' '+cls:''}"><div class="ai-agenda-item-title">${esc(item.title||'')}${item.owner?` <span style="font-size:12px;font-weight:400;color:var(--muted)">— ${esc(item.owner)}</span>`:''}</div>${item.detail?`<div class="ai-agenda-item-detail">${esc(item.detail)}</div>`:''}</div>`;});html+='</div>';});
    if(agenda.closing_note){html+=`<div style="margin-top:16px;padding:12px 14px;background:var(--al);border-radius:var(--rs);font-size:13px;color:var(--accent-dark);font-style:italic">💙 ${esc(agenda.closing_note)}</div>`;}
    html+='</div>';if(out){out.style.display='';out.innerHTML=html;}
  }catch(e){if(out){out.style.display='';out.innerHTML=`<div class="ai-agenda-output"><div style="color:var(--danger);font-size:14px">Could not generate agenda. Please try again.</div></div>`;}}
  finally{if(btn){btn.disabled=false;btn.textContent='✨ Generate Meeting Agenda';}}
}
function showNotif(msg){const b=g('notif'),t=g('notifTxt');if(!b||!t)return;t.textContent=msg;b.classList.add('show');clearTimeout(notifTimer);notifTimer=setTimeout(()=>b.classList.remove('show'),3200);}
function showLoader(msg){const o=g('loader'),m=g('loaderMsg');if(o)o.classList.remove('gone');if(m)m.textContent=msg||'Loading...';}
function hideLoader(){const o=g('loader');if(o)o.classList.add('gone');}
function g(id){return document.getElementById(id);}
function uid(){return Math.random().toString(36).slice(2,9);}
function ini(n){if(!n)return'?';return n.trim().split(' ').map(x=>x[0]).slice(0,2).join('').toUpperCase();}
function ago(ts){const d=Date.now()-ts;if(d<60000)return'just now';if(d<3600000)return Math.floor(d/60000)+'m ago';if(d<86400000)return Math.floor(d/3600000)+'h ago';return Math.floor(d/86400000)+'d ago';}
function fmtDT(ts){const d=new Date(ts);return d.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'})+' at '+d.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});}
function esc(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');}
init();
</script>
</body>
</html>
