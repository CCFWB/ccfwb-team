
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="CCFWB Jobs">
<title>CCFWB Employment Team</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#F7F4EF;--surface:#fff;--surface2:#F0EDE7;--border:#DDD9D1;
  --text:#1A1714;--muted:#7A7570;
  --accent:#3D6B4F;--accent-light:#EAF2ED;
  --warn:#C17B2A;--warn-light:#FDF3E3;
  --danger:#A33030;--danger-light:#FDEAEA;
  --cat-Events:#3D6B4F;--cat-Events-bg:#EAF2ED;
  --cat-Projects:#2C5282;--cat-Projects-bg:#EBF2FB;
  --cat-Administrative:#744210;--cat-Administrative-bg:#FEFCE8;
  --cat-Volunteer:#6B2FA0;--cat-Volunteer-bg:#F5EEFF;
  --person-Andy:#1A4A7A;--person-Andy-bg:#E8F0FA;
  --person-Kaitlyn:#7A3A1A;--person-Kaitlyn-bg:#FAF0E8;
  --person-Angie:#1A5C3A;--person-Angie-bg:#E8F5EE;
  --radius:12px;--radius-sm:8px;
  --shadow:0 1px 3px rgba(0,0,0,0.07),0 4px 12px rgba(0,0,0,0.04);
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;font-size:15px;line-height:1.5}

/* ── SETUP ── */
.setup-screen{position:fixed;inset:0;background:var(--accent);z-index:200;display:flex;flex-direction:column;justify-content:center;padding:32px 24px;overflow-y:auto}
.setup-screen.hidden{display:none}
.setup-logo{font-family:'DM Serif Display',serif;font-size:28px;color:white;margin-bottom:6px;line-height:1.2}
.setup-sub{font-size:12px;letter-spacing:0.1em;text-transform:uppercase;color:rgba(255,255,255,0.6);margin-bottom:28px}
.setup-card{background:white;border-radius:var(--radius);padding:18px;margin-bottom:14px}
.setup-card h3{font-size:14px;font-weight:500;margin-bottom:6px;color:var(--text)}
.setup-card p{font-size:12px;color:var(--muted);margin-bottom:12px;line-height:1.6}
.setup-card ol{font-size:12px;color:var(--muted);line-height:2.1;padding-left:18px}
.setup-card ol a{color:var(--accent);font-weight:500;text-decoration:none}
.setup-input{width:100%;padding:10px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--bg);margin-bottom:10px;outline:none}
.setup-input:focus{border-color:var(--accent);background:white}
.setup-btn{width:100%;padding:13px;background:var(--accent);color:white;border:none;border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:15px;font-weight:500;cursor:pointer;margin-top:2px}
.setup-btn:disabled{opacity:0.5}
.setup-btn-outline{width:100%;padding:11px;background:transparent;color:rgba(255,255,255,0.75);border:1px solid rgba(255,255,255,0.3);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer;margin-top:8px}
.setup-err{font-size:12px;color:var(--danger);margin-top:8px;display:none;background:var(--danger-light);padding:8px 10px;border-radius:6px}
.bin-copy{font-size:12px;color:var(--accent);background:var(--accent-light);padding:8px 12px;border-radius:var(--radius-sm);word-break:break-all;cursor:pointer;margin-top:8px;display:none}

/* ── SYNC BAR ── */
.sync-bar{background:var(--surface);border-bottom:1px solid var(--border);padding:6px 16px;display:flex;align-items:center;gap:8px;font-size:12px;color:var(--muted)}
.sync-dot{width:7px;height:7px;border-radius:50%;background:var(--border);flex-shrink:0;transition:background 0.3s}
.sync-dot.syncing{background:var(--warn);animation:blink 0.8s infinite}
.sync-dot.synced{background:var(--accent)}
.sync-dot.error{background:var(--danger)}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0.3}}
.sync-label{flex:1}
.sync-action{background:none;border:none;color:var(--accent);font-size:12px;font-family:'DM Sans',sans-serif;cursor:pointer;padding:2px 6px}

/* ── NOTIF ── */
.notif-badge{position:fixed;top:12px;right:12px;z-index:150;background:var(--surface);border:1px solid var(--border);border-radius:20px;padding:6px 14px 6px 10px;display:flex;align-items:center;gap:7px;font-size:12px;color:var(--accent);font-weight:500;box-shadow:var(--shadow);opacity:0;transform:translateY(-8px);transition:opacity 0.3s,transform 0.3s;pointer-events:none}
.notif-badge.show{opacity:1;transform:translateY(0)}
.notif-dot{width:7px;height:7px;border-radius:50%;background:var(--accent);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}

/* ── HEADER ── */
.header{background:var(--accent);color:white;padding:48px 20px 18px;position:relative;overflow:hidden}
.header::before{content:'';position:absolute;top:-40px;right:-40px;width:180px;height:180px;border-radius:50%;background:rgba(255,255,255,0.06)}
.header-sub{font-size:11px;letter-spacing:0.12em;text-transform:uppercase;opacity:0.7;margin-bottom:4px}
.header h1{font-family:'DM Serif Display',serif;font-size:26px;font-weight:400;line-height:1.2}
.header-meta{display:flex;align-items:center;gap:8px;margin-top:10px;flex-wrap:wrap}
.header-stat{font-size:12px;opacity:0.8;background:rgba(255,255,255,0.15);padding:4px 10px;border-radius:20px}
.settings-btn{margin-left:auto;background:rgba(255,255,255,0.15);border:none;color:white;font-size:15px;width:30px;height:30px;border-radius:50%;cursor:pointer}

/* ── TABS ── */
.tab-group-label{font-size:10px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);padding:8px 16px 2px;background:var(--surface);border-bottom:none;font-weight:500}
.tabs{background:var(--surface);border-bottom:1px solid var(--border);display:flex;overflow-x:auto;scrollbar-width:none;padding:0 8px;gap:2px}
.tabs::-webkit-scrollbar{display:none}
.tab{padding:10px 12px;font-size:13px;font-weight:500;color:var(--muted);border-bottom:2px solid transparent;white-space:nowrap;cursor:pointer;transition:color 0.15s,border-color 0.15s;background:none;border-top:none;border-left:none;border-right:none;font-family:'DM Sans',sans-serif;position:relative}
.tab.active{color:var(--accent);border-bottom-color:var(--accent)}
.tab.person-tab.active{color:var(--accent);border-bottom-color:var(--accent)}
.tab-divider{width:1px;background:var(--border);margin:8px 4px;flex-shrink:0}

/* badge on tab */
.tab-count{display:inline-flex;align-items:center;justify-content:center;min-width:16px;height:16px;border-radius:8px;font-size:10px;font-weight:500;padding:0 4px;margin-left:5px;background:var(--surface2);color:var(--muted);line-height:1}
.tab.active .tab-count{background:var(--accent-light);color:var(--accent)}
.tab-count.has-items{background:var(--warn-light);color:var(--warn)}
.tab.active .tab-count.has-items{background:var(--warn-light);color:var(--warn)}
.tab-count.orphan-count{background:var(--danger-light);color:var(--danger)}
.tab.active .tab-count.orphan-count{background:var(--danger-light);color:var(--danger)}

/* ── MAIN ── */
.main{padding:16px;max-width:600px;margin:0 auto}

/* summary */
.summary-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:20px}
.summary-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-sm);padding:12px;text-align:center}
.summary-card .num{font-family:'DM Serif Display',serif;font-size:28px;line-height:1;margin-bottom:4px}
.summary-card .lbl{font-size:11px;color:var(--muted);letter-spacing:0.05em;text-transform:uppercase}
.num-todo{color:var(--muted)}.num-prog{color:var(--warn)}.num-done{color:var(--accent)}

/* view header */
.view-header{display:flex;align-items:center;gap:10px;margin-bottom:16px}
.view-avatar{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:500;flex-shrink:0}
.view-title{font-family:'DM Serif Display',serif;font-size:20px;font-weight:400}
.view-sub{font-size:12px;color:var(--muted);margin-top:1px}

/* section label */
.section-label{font-size:11px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);font-weight:500;margin:18px 0 10px}

/* task card */
.task-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:14px 16px;margin-bottom:10px;box-shadow:var(--shadow);position:relative}
.task-card.new-flash{animation:flash-in 1.4s ease}
@keyframes flash-in{0%{background:var(--accent-light)}100%{background:var(--surface)}}
.task-card-top{display:flex;align-items:flex-start;gap:10px}
.task-name{font-weight:500;font-size:15px;flex:1;line-height:1.4}
.task-meta{display:flex;align-items:center;gap:6px;margin-top:8px;flex-wrap:wrap}
.cat-badge{font-size:11px;font-weight:500;padding:3px 8px;border-radius:20px}
.cat-Events{background:var(--cat-Events-bg);color:var(--cat-Events)}
.cat-Projects{background:var(--cat-Projects-bg);color:var(--cat-Projects)}
.cat-Administrative{background:var(--cat-Administrative-bg);color:var(--cat-Administrative)}
.cat-Volunteer{background:var(--cat-Volunteer-bg);color:var(--cat-Volunteer)}
.owner-chip{font-size:11px;color:var(--muted);display:flex;align-items:center;gap:4px}
.owner-dot{width:18px;height:18px;border-radius:50%;background:var(--surface2);border:1px solid var(--border);font-size:9px;font-weight:500;display:flex;align-items:center;justify-content:center;color:var(--text)}
.task-notes{font-size:13px;color:var(--muted);margin-top:8px;line-height:1.5;border-left:2px solid var(--border);padding-left:10px}
.status-toggle{display:flex;gap:4px;margin-top:10px}
.status-btn{flex:1;padding:6px 4px;font-size:11px;font-weight:500;border-radius:6px;border:1px solid var(--border);background:var(--bg);color:var(--muted);cursor:pointer;transition:all 0.15s;font-family:'DM Sans',sans-serif;text-align:center}
.status-btn.active-not{background:var(--surface2);color:var(--text);border-color:var(--border)}
.status-btn.active-prog{background:var(--warn-light);color:var(--warn);border-color:var(--warn)}
.status-btn.active-done{background:var(--accent-light);color:var(--accent);border-color:var(--accent)}
.delete-btn{background:none;border:none;color:var(--border);font-size:18px;cursor:pointer;padding:2px 4px;line-height:1;transition:color 0.2s;font-family:'DM Sans',sans-serif}
.timestamp{font-size:11px;color:var(--muted);margin-left:auto}
.date-row{display:flex;align-items:center;gap:10px;margin-top:8px;flex-wrap:wrap}
.date-chip{display:inline-flex;align-items:center;gap:4px;font-size:11px;padding:3px 8px;border-radius:20px;font-weight:500}
.date-chip.age{background:var(--surface2);color:var(--muted)}
.date-chip.age.old{background:#FDF3E3;color:#8B5E1A}
.date-chip.age.stale{background:var(--danger-light);color:var(--danger)}
.date-chip.due{background:var(--accent-light);color:var(--accent)}
.date-chip.due.soon{background:#FDF3E3;color:var(--warn)}
.date-chip.due.overdue{background:var(--danger-light);color:var(--danger);font-weight:600}
.date-chip.due.today{background:#FFF8E1;color:#8B6914;font-weight:600}

/* notes & comments */
.notes-section{margin-top:10px;border-top:1px solid var(--surface2);padding-top:10px}
.notes-label{font-size:10px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);font-weight:500;margin-bottom:6px;display:flex;align-items:center;gap:6px}
.unread-badge{display:inline-flex;align-items:center;justify-content:center;min-width:16px;height:16px;border-radius:8px;font-size:10px;font-weight:600;padding:0 4px;background:var(--danger);color:white;animation:pulse-badge 2s infinite}
@keyframes pulse-badge{0%,100%{opacity:1}50%{opacity:0.6}}
.notes-display{font-size:13px;color:var(--muted);line-height:1.5;border-left:2px solid var(--border);padding-left:10px;cursor:pointer;min-height:20px}
.notes-display:hover{border-left-color:var(--accent);color:var(--text)}
.notes-edit{width:100%;padding:8px 10px;border:1px solid var(--accent);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);background:white;resize:vertical;min-height:60px;outline:none;display:none}
.notes-edit-actions{display:none;gap:6px;margin-top:6px}
.notes-save-btn{padding:5px 14px;background:var(--accent);color:white;border:none;border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:12px;font-weight:500;cursor:pointer}
.notes-cancel-btn{padding:5px 10px;background:none;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:12px;color:var(--muted);cursor:pointer}
.comments-section{margin-top:10px;border-top:1px solid var(--surface2);padding-top:10px}
.comment-item{display:flex;gap:8px;margin-bottom:8px;align-items:flex-start}
.comment-item.unread .comment-dot{background:var(--danger)}
.comment-item.unread .comment-text{font-weight:500}
.comment-dot{width:6px;height:6px;border-radius:50%;background:var(--border);flex-shrink:0;margin-top:5px}
.comment-body{flex:1}
.comment-text{font-size:13px;color:var(--text);line-height:1.4}
.comment-meta{font-size:11px;color:var(--muted);margin-top:2px}
.comment-author{font-weight:500;color:var(--text)}
.comment-datetime{color:var(--muted)}
.comment-input-wrap{margin-top:8px;background:var(--bg);border:1px solid var(--border);border-radius:var(--radius-sm);padding:10px 12px}
.comment-author-row{display:flex;align-items:center;gap:8px;margin-bottom:8px}
.comment-author-label{font-size:11px;color:var(--muted);white-space:nowrap}
.comment-author-select{flex:1;padding:5px 8px;border:1px solid var(--border);border-radius:6px;font-family:'DM Sans',sans-serif;font-size:12px;color:var(--text);background:white;appearance:none;-webkit-appearance:none;outline:none}
.comment-author-select:focus{border-color:var(--accent)}
.comment-input-row{display:flex;gap:6px}
.comment-input{flex:1;padding:8px 10px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);background:white;outline:none;resize:none;min-height:36px}
.comment-input:focus{border-color:var(--accent)}
.comment-submit{padding:8px 12px;background:var(--accent);color:white;border:none;border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:12px;font-weight:500;cursor:pointer;white-space:nowrap;align-self:flex-end}
.expand-btn{font-size:11px;color:var(--accent);background:none;border:none;cursor:pointer;font-family:'DM Sans',sans-serif;padding:4px 0;margin-top:2px;display:block}
.task-card.has-unread{border-left:3px solid var(--danger)}

/* ── AGENDA & MEETINGS ── */
.meeting-panel{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:16px;margin-bottom:12px;box-shadow:var(--shadow)}
.meeting-panel-title{font-family:'DM Serif Display',serif;font-size:18px;font-weight:400;color:var(--text);margin-bottom:4px}
.meeting-panel-sub{font-size:12px;color:var(--muted);margin-bottom:14px}
.meeting-date-label{font-size:11px;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);font-weight:500;margin-bottom:8px;margin-top:16px}
.meeting-date-label:first-child{margin-top:0}
.agenda-item{display:flex;align-items:flex-start;gap:10px;padding:10px 12px;background:var(--bg);border:1px solid var(--border);border-radius:var(--radius-sm);margin-bottom:8px}
.agenda-item-dot{width:8px;height:8px;border-radius:50%;background:var(--accent);flex-shrink:0;margin-top:5px}
.agenda-item-body{flex:1}
.agenda-item-topic{font-size:14px;font-weight:500;color:var(--text);line-height:1.4}
.agenda-item-meta{font-size:11px;color:var(--muted);margin-top:3px}
.agenda-item-details{font-size:13px;color:var(--muted);margin-top:4px;line-height:1.4}
.agenda-item.discussed{opacity:0.5}
.agenda-item.discussed .agenda-item-topic{text-decoration:line-through}
.agenda-check{width:20px;height:20px;border-radius:4px;border:1px solid var(--border);background:white;cursor:pointer;flex-shrink:0;margin-top:2px;display:flex;align-items:center;justify-content:center;font-size:12px}
.agenda-check.checked{background:var(--accent-light);border-color:var(--accent);color:var(--accent)}
.small-btn{padding:6px 12px;border-radius:var(--radius-sm);border:1px solid var(--border);background:var(--surface);color:var(--muted);font-family:'DM Sans',sans-serif;font-size:12px;cursor:pointer;transition:all 0.15s}
.small-btn.primary{background:var(--accent);color:white;border-color:var(--accent)}
.add-agenda-form{background:var(--bg);border:1px solid var(--border);border-radius:var(--radius-sm);padding:12px;margin-top:10px;display:none}
.meeting-notes-body{width:100%;min-height:120px;padding:10px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:13px;color:var(--text);background:var(--bg);resize:vertical;outline:none;line-height:1.6}
.meeting-notes-body:focus{border-color:var(--accent);background:white}
.attachment-list{margin-top:10px;display:flex;flex-wrap:wrap;gap:8px}
.attachment-chip{display:inline-flex;align-items:center;gap:6px;padding:5px 10px;background:var(--cat-projects-bg);color:var(--cat-projects);border-radius:20px;font-size:12px;font-weight:500;text-decoration:none}
.upload-area{border:1px dashed var(--border);border-radius:var(--radius-sm);padding:14px;text-align:center;font-size:12px;color:var(--muted);cursor:pointer;margin-top:10px;transition:border-color 0.2s}
.upload-area:hover{border-color:var(--accent);color:var(--accent)}
.upload-input{display:none}
.cloudinary-setup{font-size:11px;color:var(--warn);background:var(--warn-light);padding:8px 10px;border-radius:var(--radius-sm);margin-bottom:12px;line-height:1.6}
.new-meeting-btn{width:100%;padding:12px;border:1px dashed var(--border);border-radius:var(--radius-sm);font-family:'DM Serif Display',serif;font-size:15px;font-weight:400;color:var(--muted);background:none;cursor:pointer;margin-bottom:12px;transition:all 0.15s}
.new-meeting-btn:hover{border-color:var(--accent);color:var(--accent)}
.meeting-row{display:flex;align-items:center;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--surface2);cursor:pointer}
.meeting-row:last-child{border-bottom:none}
.meeting-row:hover .meeting-row-title{color:var(--accent)}
.meeting-row-title{font-weight:500;font-size:14px}
.meeting-row-meta{font-size:12px;color:var(--muted)}
.meeting-detail-back{display:flex;align-items:center;gap:6px;font-size:13px;color:var(--accent);cursor:pointer;margin-bottom:16px;background:none;border:none;font-family:'DM Sans',sans-serif;padding:0}
.section-divider{height:1px;background:var(--border);margin:16px 0}
.tab-count.agenda-count{background:var(--cat-projects-bg);color:var(--cat-projects)}

/* orphan note */
.orphan-banner{background:var(--danger-light);border:1px solid #f5c0c0;border-radius:var(--radius-sm);padding:10px 14px;font-size:12px;color:var(--danger);margin-bottom:16px;line-height:1.5}

/* add form */
.add-panel{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:16px;margin-bottom:16px;box-shadow:var(--shadow)}
.add-panel h3{font-family:'DM Serif Display',serif;font-size:17px;font-weight:400;margin-bottom:14px;color:var(--text)}
.form-row{margin-bottom:12px}
.form-row label{font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px}
.form-row input,.form-row select,.form-row textarea{width:100%;padding:10px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;color:var(--text);background:var(--bg);appearance:none;-webkit-appearance:none;outline:none}
.form-row textarea{resize:vertical;min-height:72px}
.form-row input:focus,.form-row select:focus,.form-row textarea:focus{border-color:var(--accent);background:white}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.add-btn{width:100%;padding:13px;background:var(--accent);color:white;border:none;border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:15px;font-weight:500;cursor:pointer;transition:opacity 0.2s,transform 0.1s;margin-top:4px}
.add-btn:disabled{opacity:0.5}
.add-btn:active{transform:scale(0.98)}

/* report */
.report-section{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:16px;margin-bottom:12px}
.report-section h3{font-family:'DM Serif Display',serif;font-size:17px;font-weight:400;margin-bottom:14px;padding-bottom:10px;border-bottom:1px solid var(--border)}
.report-row{display:flex;justify-content:space-between;align-items:center;padding:7px 0;border-bottom:1px solid var(--surface2);font-size:13px}
.report-row:last-child{border-bottom:none}
.report-row .label{color:var(--muted)}
.report-badge{font-size:11px;font-weight:500;padding:2px 8px;border-radius:20px}
.badge-not{background:var(--surface2);color:var(--muted)}
.badge-prog{background:var(--warn-light);color:var(--warn)}
.badge-done{background:var(--accent-light);color:var(--accent)}
.member-block{margin-bottom:14px}
.member-header{display:flex;align-items:center;gap:8px;margin-bottom:8px}
.member-avatar-sm{width:28px;height:28px;border-radius:50%;font-size:11px;font-weight:500;display:flex;align-items:center;justify-content:center}

.empty{text-align:center;padding:32px 20px;color:var(--muted);font-size:14px}
.bottom-pad{height:40px}

/* loading */
.loading-overlay{position:fixed;inset:0;background:rgba(247,244,239,0.88);z-index:100;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:12px;font-size:14px;color:var(--muted)}
.loading-overlay.hidden{display:none}
.spinner{width:28px;height:28px;border:2px solid var(--border);border-top-color:var(--accent);border-radius:50%;animation:spin 0.7s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
</style>
</head>
<body>

<!-- SETUP -->
<div class="setup-screen" id="setupScreen">
  <div class="setup-logo">CCFWB<br>Team</div>
  <div class="setup-sub">One-time setup</div>
  <div class="setup-card">
    <h3>Step 1 — Create a free JSONBin account</h3>
    <ol>
      <li>Go to <a href="https://jsonbin.io" target="_blank">jsonbin.io</a> and sign up free</li>
      <li>Go to <strong>API Keys</strong> and create a new key</li>
      <li>Copy the key and paste it below</li>
    </ol>
  </div>
  <div class="setup-card">
    <h3>Step 2 — Connect</h3>
    <p>First person sets up and shares the Bin ID with teammates. Teammates enter the same Bin ID.</p>
    <input class="setup-input" type="password" id="apiKeyInput" placeholder="API Key (from JSONBin)" autocomplete="off" />
    <input class="setup-input" type="text" id="binIdInput" placeholder="Bin ID — leave blank to create new" autocomplete="off" />
    <button class="setup-btn" id="connectBtn" onclick="connectBin()">Connect & Sync</button>
    <div class="bin-copy" id="binCopyBox" onclick="copyBinId()"></div>
    <div class="setup-err" id="setupErr"></div>
  </div>
  <button class="setup-btn-outline" onclick="useDemoMode()">Skip — use offline demo</button>
</div>

<!-- LOADING -->
<div class="loading-overlay hidden" id="loadingOverlay">
  <div class="spinner"></div>
  <span id="loadingMsg">Loading tasks...</span>
</div>

<!-- NOTIF -->
<div class="notif-badge" id="notifBadge">
  <div class="notif-dot"></div>
  <span id="notifText">Synced</span>
</div>

<!-- HEADER -->
<div class="header" id="appHeader" style="display:none">
  <div class="header-sub">Calvary Chapel Fort Walton Beach</div>
  <h1>Team</h1>
  <div class="header-meta">
    <div class="header-stat" id="headerStat">—</div>
    <button class="settings-btn" onclick="showSettings()">⚙</button>
  </div>
</div>

<!-- SYNC BAR -->
<div class="sync-bar" id="syncBar" style="display:none">
  <div class="sync-dot" id="syncDot"></div>
  <span class="sync-label" id="syncLabel">Connecting...</span>
  <button class="sync-action" onclick="pullTasks()">Refresh</button>
</div>

<!-- TABS -->
<div id="appTabs" style="display:none">
  <div class="tabs">
    <button class="tab person-tab active" id="tab-btn-Andy"    onclick="switchTab('Andy')">Pastor Andy<span class="tab-count" id="tc-Andy">0</span></button>
    <button class="tab person-tab"        id="tab-btn-Kaitlyn" onclick="switchTab('Kaitlyn')">Kaitlyn<span class="tab-count" id="tc-Kaitlyn">0</span></button>
    <button class="tab person-tab"        id="tab-btn-Angie"   onclick="switchTab('Angie')">Angie<span class="tab-count" id="tc-Angie">0</span></button>
    <div class="tab-divider"></div>
    <button class="tab" id="tab-btn-Events"    onclick="switchTab('Events')">Events<span class="tab-count" id="tc-Events">0</span></button>
    <button class="tab" id="tab-btn-Volunteer" onclick="switchTab('Volunteer')">Volunteers<span class="tab-count" id="tc-Volunteer">0</span></button>
    <button class="tab" id="tab-btn-Projects"  onclick="switchTab('Projects')">Projects<span class="tab-count" id="tc-Projects">0</span></button>
    <div class="tab-divider"></div>
    <button class="tab" id="tab-btn-orphaned"  onclick="switchTab('orphaned')">Orphaned<span class="tab-count orphan-count" id="tc-orphaned">0</span></button>
    <div class="tab-divider"></div>
    <button class="tab" id="tab-btn-agenda"   onclick="switchTab('agenda')">Agenda<span class="tab-count agenda-count" id="tc-agenda">0</span></button>
    <button class="tab" id="tab-btn-meetings" onclick="switchTab('meetings')">Meetings</button>
    <div class="tab-divider"></div>
    <button class="tab" id="tab-btn-add"    onclick="switchTab('add')">+ Add</button>
    <button class="tab" id="tab-btn-report" onclick="switchTab('report')">Report</button>
  </div>
</div>

<div class="main" id="appMain" style="display:none">

  <!-- PERSON / CATEGORY TASK VIEW -->
  <div id="tab-view">
    <div id="view-header-area"></div>
    <div class="summary-grid">
      <div class="summary-card"><div class="num num-todo" id="cnt-todo">0</div><div class="lbl">Not Started</div></div>
      <div class="summary-card"><div class="num num-prog" id="cnt-prog">0</div><div class="lbl">In Progress</div></div>
      <div class="summary-card"><div class="num num-done" id="cnt-done">0</div><div class="lbl">Complete</div></div>
    </div>
    <div id="view-sections"></div>
    <div id="empty-view" class="empty" style="display:none">No tasks here yet.</div>
  </div>

  <!-- ADD -->
  <div id="tab-add" style="display:none">
    <div class="add-panel">
      <h3>Log a Task</h3>
      <div class="form-row"><label>Task Name</label><input type="text" id="inp-name" placeholder="What needs to be done?" /></div>
      <div class="form-grid">
        <div class="form-row"><label>Category</label>
          <select id="inp-cat">
            <option value="Events">Events</option>
            <option value="Projects">Special Projects</option>
            <option value="Administrative">Administrative</option>
            <option value="Volunteer">Volunteer Management</option>
          </select>
        </div>
        <div class="form-row"><label>Owner</label>
          <select id="inp-owner">
            <option value="">— Unassigned —</option>
            <option value="Pastor Andy">Pastor Andy</option>
            <option value="Kaitlyn">Kaitlyn</option>
            <option value="Angie">Angie</option>
          </select>
        </div>
      </div>
      <div class="form-row"><label>Status</label>
        <select id="inp-status">
          <option value="not">Not Started</option>
          <option value="prog">In Progress</option>
          <option value="done">Complete</option>
        </select>
      </div>
      <div class="form-row"><label>Target Date (optional)</label><input type="date" id="inp-due" /></div>
      <div class="form-row"><label>Notes (optional)</label><textarea id="inp-notes" placeholder="Any details, context, or updates..."></textarea></div>
      <button class="add-btn" id="addBtn" onclick="addTask()">Add Task</button>
    </div>
  </div>

  <!-- REPORT -->
  <div id="tab-report" style="display:none"><div id="report-content"></div></div>

  <!-- AGENDA -->
  <div id="tab-agenda" style="display:none">
    <div class="meeting-panel">
      <div class="meeting-panel-title">Meeting Agenda</div>
      <div class="meeting-panel-sub">Add topics for the next meeting. Anyone can contribute.</div>
      <div id="agenda-meeting-selector-wrap">
        <select class="meeting-select" id="agenda-meeting-select" onchange="renderAgendaForMeeting()">
          <option value="">— Select or create a meeting —</option>
        </select>
      </div>
      <button class="new-meeting-btn" onclick="showNewMeetingForm('agenda')">+ Schedule a new meeting</button>
      <div class="add-agenda-form" id="new-meeting-form">
        <div class="form-row" style="margin-bottom:10px"><label style="font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px">Meeting Date</label>
          <input type="date" id="new-meeting-date" style="width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;outline:none" />
        </div>
        <div class="form-row" style="margin-bottom:10px"><label style="font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px">Meeting Title (optional)</label>
          <input type="text" id="new-meeting-title" placeholder="e.g. Weekly Team Meeting" style="width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;outline:none" />
        </div>
        <div style="display:flex;gap:8px">
          <button class="small-btn primary" onclick="createMeeting()">Create Meeting</button>
          <button class="small-btn" onclick="hideNewMeetingForm()">Cancel</button>
        </div>
      </div>
    </div>
    <div id="agenda-items-panel" style="display:none">
      <div class="meeting-panel">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:12px">
          <div>
            <div class="meeting-panel-title" id="agenda-meeting-title-display">Agenda</div>
            <div class="meeting-panel-sub" id="agenda-meeting-date-display"></div>
          </div>
          <button class="small-btn primary" onclick="showAddTopicForm()">+ Add Topic</button>
        </div>
        <div class="add-agenda-form" id="add-topic-form">
          <div class="form-row" style="margin-bottom:8px">
            <label style="font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px">Topic</label>
            <input type="text" id="topic-text" placeholder="What do you want to discuss?" style="width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;outline:none" />
          </div>
          <div class="form-row" style="margin-bottom:8px">
            <label style="font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px">Details (optional)</label>
            <textarea id="topic-details" placeholder="Any background info..." style="width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:13px;outline:none;resize:vertical;min-height:60px"></textarea>
          </div>
          <div class="form-row" style="margin-bottom:10px">
            <label style="font-size:11px;text-transform:uppercase;letter-spacing:0.08em;color:var(--muted);display:block;margin-bottom:5px">Added by</label>
            <select id="topic-author" style="width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:14px;outline:none;appearance:none;background:var(--bg)">
              <option value="">— Select your name —</option>
              <option value="Pastor Andy">Pastor Andy</option>
              <option value="Kaitlyn">Kaitlyn</option>
              <option value="Angie">Angie</option>
            </select>
          </div>
          <div style="display:flex;gap:8px">
            <button class="small-btn primary" onclick="addAgendaTopic()">Add Topic</button>
            <button class="small-btn" onclick="hideAddTopicForm()">Cancel</button>
          </div>
        </div>
        <div id="agenda-items-list" style="margin-top:12px"></div>
        <div id="agenda-empty" style="text-align:center;padding:20px;color:var(--muted);font-size:13px;display:none">No topics yet — be the first to add one.</div>
      </div>
    </div>
  </div>

  <!-- MEETINGS -->
  <div id="tab-meetings" style="display:none">
    <div id="meetings-list-view">
      <div class="meeting-panel">
        <div class="meeting-panel-title">Meeting Notes</div>
        <div class="meeting-panel-sub">Notes and attachments organized by meeting date.</div>
        <button class="new-meeting-btn" onclick="showNewMeetingForm('meetings')">+ Add a meeting</button>
        <div id="meetings-list"></div>
        <div id="meetings-empty" style="text-align:center;padding:20px;color:var(--muted);font-size:13px">No meetings yet.</div>
      </div>
    </div>
    <div id="meetings-detail-view" style="display:none">
      <button class="meeting-detail-back" onclick="closeMeetingDetail()">← Back to meetings</button>
      <div class="meeting-panel">
        <div class="meeting-panel-title" id="detail-meeting-title"></div>
        <div class="meeting-panel-sub" id="detail-meeting-date"></div>
        <div class="section-divider"></div>
        <div class="notes-label" style="margin-bottom:8px">Notes</div>
        <textarea class="meeting-notes-body" id="detail-notes-body" placeholder="Type meeting notes here..."></textarea>
        <div style="display:flex;gap:8px;margin-top:8px">
          <button class="small-btn primary" onclick="saveMeetingNotes()">Save Notes</button>
        </div>
        <div class="section-divider"></div>
        <div class="notes-label" style="margin-bottom:8px">Attachments</div>
        <div id="cloudinary-setup-banner" class="cloudinary-setup" style="display:none">
          To enable file uploads, add your Cloudinary details in ⚙ Settings. Get a free account at <strong>cloudinary.com</strong>.
        </div>
        <div class="attachment-list" id="detail-attachments"></div>
        <label class="upload-area" for="file-upload-input">
          📎 Tap to attach a photo or document
        </label>
        <input type="file" class="upload-input" id="file-upload-input" accept="image/*,.pdf,.doc,.docx" onchange="handleFileUpload(event)" />
        <div id="upload-progress" style="font-size:12px;color:var(--muted);margin-top:6px;display:none">Uploading...</div>
      </div>
    </div>
  </div>

  <div class="bottom-pad"></div>
</div>

<script>
const CREDS_KEY='ccfwb_creds_v2', LOCAL_KEY='ccfwb_tasks_v3', POLL_MS=15000;
const READ_KEY='ccfwb_read_v1'; // maps taskId -> last read timestamp (per device)
let creds=null, tasks=[], activeTab='Andy', pollTimer=null, lastVersion=null, isSaving=false, notifTimer=null;
let readLog={}; // { taskId: timestamp } — when this device last "saw" that task's comments

function loadReadLog(){try{readLog=JSON.parse(localStorage.getItem(READ_KEY))||{};}catch(e){readLog={};}}
function saveReadLog(){localStorage.setItem(READ_KEY,JSON.stringify(readLog));}
function markTaskRead(id){readLog[id]=Date.now();saveReadLog();}
function getUnreadCount(t){
  if(!t.comments||!t.comments.length)return 0;
  const lastRead=readLog[t.id]||0;
  return t.comments.filter(c=>c.ts>lastRead).length;
}

const PEOPLE = [
  {key:'Andy',  label:'Pastor Andy', initials:'PA', color:'var(--person-Andy)',    bg:'var(--person-Andy-bg)',    match: t => ownerMatch(t,'Andy')},
  {key:'Kaitlyn',label:'Kaitlyn',    initials:'KA', color:'var(--person-Kaitlyn)', bg:'var(--person-Kaitlyn-bg)', match: t => ownerMatch(t,'Kaitlyn')},
  {key:'Angie', label:'Angie',       initials:'AN', color:'var(--person-Angie)',   bg:'var(--person-Angie-bg)',   match: t => ownerMatch(t,'Angie')},
];
const CATS = [
  {key:'Events',      label:'Events',              color:'var(--cat-Events)',         bg:'var(--cat-Events-bg)'},
  {key:'Volunteer',   label:'Volunteer Management',color:'var(--cat-Volunteer)',      bg:'var(--cat-Volunteer-bg)'},
  {key:'Projects',    label:'Special Projects',    color:'var(--cat-Projects)',       bg:'var(--cat-Projects-bg)'},
  {key:'Administrative',label:'Administrative',    color:'var(--cat-Administrative)', bg:'var(--cat-Administrative-bg)'},
];
const ALL_TABS = ['Andy','Kaitlyn','Angie','Events','Volunteer','Projects','orphaned','agenda','meetings','add','report'];
let meetings=[]; // [{id,date,title,notes,attachments,agendaItems}]
let activeMeetingId=null;

function ownerMatch(t, key) {
  if (!t.owner) return false;
  return t.owner.toLowerCase().includes(key.toLowerCase());
}

// ── INIT ──────────────────────────────────────────────────────────────────────
function init() {
  loadReadLog();
  try { creds=JSON.parse(localStorage.getItem(CREDS_KEY)); } catch(e){}
  if (creds) {
    showApp();
    if (creds.demoMode) { loadLocal(); renderAll(); setSyncStatus('demo','Offline demo mode'); }
    else { pullTasks(true); startPolling(); }
  }
}

function showApp() {
  document.getElementById('setupScreen').classList.add('hidden');
  ['appHeader','syncBar','appTabs','appMain'].forEach(id=>document.getElementById(id).style.display='');
}

// ── SETUP ─────────────────────────────────────────────────────────────────────
async function connectBin() {
  const apiKey=document.getElementById('apiKeyInput').value.trim();
  const existingBin=document.getElementById('binIdInput').value.trim();
  if (!apiKey){showSetupErr('Please enter your API key.');return;}
  const btn=document.getElementById('connectBtn');
  btn.disabled=true; btn.textContent='Connecting...';
  document.getElementById('setupErr').style.display='none';
  try {
    let binId=existingBin;
    if (!binId) {
      const r=await fetch('https://api.jsonbin.io/v3/b',{method:'POST',headers:{'Content-Type':'application/json','X-Master-Key':apiKey,'X-Bin-Name':'CCFWB-Tasks','X-Private':'false'},body:JSON.stringify({tasks:[],v:1})});
      if(!r.ok) throw new Error('Invalid API key or JSONBin error ('+r.status+')');
      const d=await r.json(); binId=d.metadata.id; lastVersion=d.metadata.version;
      const box=document.getElementById('binCopyBox');
      box.textContent='Bin ID (tap to copy): '+binId; box.style.display='block';
    } else {
      const r=await fetch('https://api.jsonbin.io/v3/b/'+binId+'/latest',{headers:{'X-Master-Key':apiKey}});
      if(!r.ok) throw new Error('Could not access Bin ID. Check both values.');
      const d=await r.json(); tasks=d.record.tasks||[]; lastVersion=d.metadata.version; saveLocal();
    }
    creds={apiKey,binId,demoMode:false}; localStorage.setItem(CREDS_KEY,JSON.stringify(creds));
    showApp(); renderAll(); setSyncStatus('synced','Synced'); startPolling();
  } catch(e) {
    showSetupErr(e.message||'Connection failed. Try again.');
    btn.disabled=false; btn.textContent='Connect & Sync';
  }
}
function copyBinId(){const t=document.getElementById('binCopyBox').textContent.replace('Bin ID (tap to copy): ','');try{navigator.clipboard.writeText(t);document.getElementById('binCopyBox').textContent='Copied: '+t;}catch(e){}}
function showSetupErr(msg){const e=document.getElementById('setupErr');e.textContent=msg;e.style.display='block';document.getElementById('connectBtn').disabled=false;document.getElementById('connectBtn').textContent='Connect & Sync';}
function useDemoMode(){creds={demoMode:true};localStorage.setItem(CREDS_KEY,JSON.stringify(creds));loadLocal();showApp();renderAll();setSyncStatus('demo','Offline demo mode');}
function showSettings(){
  if(!creds||creds.demoMode){if(confirm('Offline demo mode.\n\nReset to connect?'))reset();return;}
  const opts=['1 — Copy Bin ID for teammates','2 — Set up Cloudinary (file uploads)','3 — Reset setup'];
  const choice=prompt('Settings:\n\n'+opts.join('\n')+'\n\nType 1, 2, or 3:');
  if(choice==='1'){try{navigator.clipboard.writeText(creds.binId);showNotif('Bin ID copied');}catch(e){alert('Bin ID: '+creds.binId);}}
  else if(choice==='2'){
    const cloud=prompt('Cloudinary Cloud Name:\n(from cloudinary.com dashboard)');
    if(!cloud)return;
    const preset=prompt('Upload Preset name:\n(Settings → Upload → Add upload preset → set to Unsigned)');
    if(!preset)return;
    creds.cloudinaryCloud=cloud.trim();
    creds.cloudinaryPreset=preset.trim();
    localStorage.setItem(CREDS_KEY,JSON.stringify(creds));
    showNotif('Cloudinary configured!');
    document.getElementById('cloudinary-setup-banner').style.display='none';
  }
  else if(choice==='3'){if(confirm('Reset setup?'))reset();}
}
function reset(){localStorage.removeItem(CREDS_KEY);location.reload();}

// ── SYNC ──────────────────────────────────────────────────────────────────────
function setSyncStatus(state,label){
  const dot=document.getElementById('syncDot'),lbl=document.getElementById('syncLabel');
  dot.className='sync-dot'+(state==='syncing'?' syncing':state==='synced'?' synced':state==='error'?' error':'');
  lbl.textContent=label;
}
async function pullTasks(initial){
  if(!creds||creds.demoMode)return;
  setSyncStatus('syncing','Syncing...');
  if(initial)showLoading('Loading tasks...');
  try {
    const r=await fetch('https://api.jsonbin.io/v3/b/'+creds.binId+'/latest',{headers:{'X-Master-Key':creds.apiKey}});
    if(!r.ok)throw new Error('HTTP '+r.status);
    const d=await r.json(),ver=d.metadata.version;
    if(ver!==lastVersion){
      const wasEmpty=!tasks.length;
      tasks=d.record.tasks||[]; meetings=d.record.meetings||[]; lastVersion=ver; saveLocal(); renderAll();
      if(!wasEmpty&&!initial)showNotif('Updated by teammate');
    }
    setSyncStatus('synced','Up to date · '+timeAgo(Date.now()));
  } catch(e){setSyncStatus('error','Sync error — tap Refresh');}
  finally{hideLoading();}
}
async function pushTasks(){
  if(!creds||creds.demoMode){saveLocal();return;}
  if(isSaving)return; isSaving=true; setSyncStatus('syncing','Saving...');
  try {
    const r=await fetch('https://api.jsonbin.io/v3/b/'+creds.binId,{method:'PUT',headers:{'Content-Type':'application/json','X-Master-Key':creds.apiKey},body:JSON.stringify({tasks,meetings,v:Date.now()})});
    if(!r.ok)throw new Error();
    const d=await r.json(); lastVersion=d.metadata.version; saveLocal(); setSyncStatus('synced','Saved · '+timeAgo(Date.now()));
  } catch(e){setSyncStatus('error','Save failed — tap Refresh');showNotif('Could not save');}
  finally{isSaving=false;}
}
function startPolling(){clearInterval(pollTimer);pollTimer=setInterval(pullTasks,POLL_MS);}
document.addEventListener('visibilitychange',()=>{if(!document.hidden&&creds&&!creds.demoMode)pullTasks();});

function saveLocal(){localStorage.setItem(LOCAL_KEY,JSON.stringify({tasks,meetings}));}
function loadLocal(){
  try{
    const raw=JSON.parse(localStorage.getItem(LOCAL_KEY));
    if(raw&&raw.tasks){tasks=raw.tasks;meetings=raw.meetings||[];}
    else{tasks=raw||defaultTasks();meetings=[];}
  }catch(e){tasks=defaultTasks();meetings=[];}
}
function defaultTasks(){return[
  {id:uid(),name:'Job Fair Planning',cat:'Events',owner:'Pastor Andy',status:'prog',notes:'Venue confirmed, finalize vendors',due:'',created:Date.now()-86400000*5,ts:Date.now()-86400000},
  {id:uid(),name:'Resume Workshop Setup',cat:'Events',owner:'Kaitlyn',status:'not',notes:'',due:'',created:Date.now()-86400000*3,ts:Date.now()-50000000},
  {id:uid(),name:'Volunteer Intake Process',cat:'Volunteer',owner:'Angie',status:'not',notes:'',due:'',created:Date.now()-86400000*2,ts:Date.now()-30000000},
  {id:uid(),name:'Follow up on job board',cat:'Administrative',owner:'',status:'not',notes:'Needs to be assigned',due:'',created:Date.now()-86400000,ts:Date.now()-10000000},
];}

// ── ACTIONS ───────────────────────────────────────────────────────────────────
async function addTask(){
  const name=document.getElementById('inp-name').value.trim();
  if(!name){document.getElementById('inp-name').focus();return;}
  const btn=document.getElementById('addBtn');
  btn.disabled=true; btn.textContent='Saving...';
  const task={id:uid(),name,cat:document.getElementById('inp-cat').value,owner:document.getElementById('inp-owner').value,status:document.getElementById('inp-status').value,notes:document.getElementById('inp-notes').value.trim(),due:document.getElementById('inp-due').value||'',created:Date.now(),ts:Date.now()};
  tasks.push(task);
  await pushTasks();
  document.getElementById('inp-name').value=''; document.getElementById('inp-notes').value=''; document.getElementById('inp-due').value='';
  btn.disabled=false; btn.textContent='Add Task';
  // switch to the appropriate tab
  const ownerVal=task.owner;
  if(ownerVal.includes('Andy'))switchTab('Andy');
  else if(ownerVal.includes('Kaitlyn'))switchTab('Kaitlyn');
  else if(ownerVal.includes('Angie'))switchTab('Angie');
  else switchTab('orphaned');
  renderAll(task.id);
  showNotif('Task added');
}
async function setStatus(id,status){
  const t=tasks.find(x=>x.id===id);
  if(!t||t.status===status)return;
  t.status=status; t.ts=Date.now(); renderAll(); await pushTasks(); showNotif('Status updated');
}
async function deleteTask(id){
  if(!confirm('Remove this task?'))return;
  tasks=tasks.filter(t=>t.id!==id); renderAll(); await pushTasks(); showNotif('Task removed');
}
async function assignTask(id, owner){
  const t=tasks.find(x=>x.id===id);
  if(!t)return; t.owner=owner; t.ts=Date.now(); renderAll(); await pushTasks(); showNotif('Assigned to '+owner);
}

// ── RENDER ────────────────────────────────────────────────────────────────────
function renderAll(newId){
  updateTabCounts();
  renderCurrentView(newId);
}

function updateTabCounts(){
  // people
  PEOPLE.forEach(p=>{
    const n=tasks.filter(t=>!isDone(t)&&p.match(t)).length;
    const el=document.getElementById('tc-'+p.key);
    if(el){el.textContent=n;el.className='tab-count'+(n>0?' has-items':'');}
  });
  // categories
  CATS.forEach(c=>{
    const n=tasks.filter(t=>!isDone(t)&&t.cat===c.key).length;
    const el=document.getElementById('tc-'+c.key);
    if(el){el.textContent=n;el.className='tab-count'+(n>0?' has-items':'');}
  });
  // orphaned
  const orphans=tasks.filter(t=>!isDone(t)&&!t.owner);
  const oEl=document.getElementById('tc-orphaned');
  if(oEl){oEl.textContent=orphans.length;oEl.className='tab-count'+(orphans.length>0?' orphan-count':'');}
  // agenda — count all pending topics across all meetings
  const pendingTopics=meetings.reduce((n,m)=>n+(m.agendaItems||[]).filter(a=>!a.discussed).length,0);
  const aEl=document.getElementById('tc-agenda');
  if(aEl){aEl.textContent=pendingTopics;aEl.className='tab-count'+(pendingTopics>0?' agenda-count':'');}
  // global stats
  const tot=tasks.length,dn=tasks.filter(t=>t.status==='done').length;
  document.getElementById('headerStat').textContent=tot+' task'+(tot!==1?'s':'')+' · '+dn+' complete';
}

function isDone(t){return t.status==='done';}

function renderCurrentView(newId){
  const tab=activeTab;
  if(tab==='add'||tab==='report')return;

  let filtered=[], headerHtml='', sections=[];

  if(tab==='orphaned'){
    filtered=tasks.filter(t=>!t.owner||t.owner.trim()==='');
    headerHtml=`<div class="orphan-banner">These tasks have no owner assigned. Tap a task to assign it.</div>`;
    // group orphans by category
    CATS.forEach(c=>{
      const ct=filtered.filter(t=>t.cat===c.key);
      if(ct.length)sections.push({label:c.label,color:c.color,tasks:ct});
    });
  } else {
    const person=PEOPLE.find(p=>p.key===tab);
    const cat=CATS.find(c=>c.key===tab);
    if(person){
      filtered=tasks.filter(t=>person.match(t));
      headerHtml=`<div class="view-header">
        <div class="view-avatar" style="background:${person.bg};color:${person.color}">${person.initials}</div>
        <div><div class="view-title">${person.label}</div><div class="view-sub">${filtered.length} task${filtered.length!==1?'s':''}</div></div>
      </div>`;
      // group by category
      CATS.forEach(c=>{
        const ct=filtered.filter(t=>t.cat===c.key);
        if(ct.length)sections.push({label:c.label,color:c.color,tasks:ct});
      });
      if(!filtered.length)sections=[];
    } else if(cat){
      filtered=tasks.filter(t=>t.cat===tab);
      headerHtml=`<div class="view-header">
        <div class="view-title">${cat.label}</div>
      </div>`;
      // group by owner
      const owners=[...new Set(filtered.map(t=>t.owner||'Unassigned'))];
      owners.forEach(o=>{
        const ct=filtered.filter(t=>(t.owner||'Unassigned')===o);
        sections.push({label:o==='Unassigned'?'Unassigned':o,color:o==='Unassigned'?'var(--danger)':'var(--muted)',tasks:ct});
      });
    }
  }

  // summary counts
  const todo=filtered.filter(t=>t.status==='not').length;
  const prog=filtered.filter(t=>t.status==='prog').length;
  const done=filtered.filter(t=>t.status==='done').length;
  document.getElementById('cnt-todo').textContent=todo;
  document.getElementById('cnt-prog').textContent=prog;
  document.getElementById('cnt-done').textContent=done;

  document.getElementById('view-header-area').innerHTML=headerHtml;

  const sectEl=document.getElementById('view-sections');
  sectEl.innerHTML='';

  if(!filtered.length){
    document.getElementById('empty-view').style.display='';
    return;
  }
  document.getElementById('empty-view').style.display='none';

  sections.forEach(sec=>{
    const wrap=document.createElement('div');
    const label=document.createElement('div');
    label.className='section-label';
    label.style.color=sec.color;
    label.textContent=sec.label;
    wrap.appendChild(label);
    sec.tasks.forEach(t=>{
      wrap.appendChild(buildCard(t,newId,tab));
    });
    sectEl.appendChild(wrap);
  });
}

function buildCard(t, newId, currentTab){
  const d=document.createElement('div');
  d.className='task-card'+(t.id===newId?' new-flash':'');
  const catObj=CATS.find(c=>c.key===t.cat)||{label:t.cat,bg:'var(--surface2)',color:'var(--muted)'};
  const isOrphan=!t.owner||t.owner.trim()==='';
  const ownerHtml=isOrphan
    ? `<span style="font-size:11px;color:var(--danger);background:var(--danger-light);padding:2px 8px;border-radius:20px">Unassigned</span>`
    : `<span class="owner-chip"><span class="owner-dot">${ini(t.owner)}</span>${esc(t.owner)}</span>`;

  // Age chip
  const createdTs=t.created||t.ts;
  const ageDays=Math.floor((Date.now()-createdTs)/86400000);
  let ageClass='age',ageLabel='';
  if(ageDays===0)ageLabel='Created today';
  else if(ageDays===1)ageLabel='1 day old';
  else ageLabel=ageDays+' days old';
  if(ageDays>=14)ageClass='age stale';
  else if(ageDays>=7)ageClass='age old';
  const ageChip=`<span class="date-chip ${ageClass}">⏱ ${ageLabel}</span>`;

  // Due date chip
  let dueChip='';
  if(t.due&&t.status!=='done'){
    const dueDate=new Date(t.due+'T00:00:00');
    const today=new Date();today.setHours(0,0,0,0);
    const diffDays=Math.round((dueDate-today)/86400000);
    const fmtDue=dueDate.toLocaleDateString('en-US',{month:'short',day:'numeric'});
    let dueClass='due',dueLabel='';
    if(diffDays<0){dueClass='due overdue';dueLabel=`Overdue by ${Math.abs(diffDays)}d`;}
    else if(diffDays===0){dueClass='due today';dueLabel='Due today';}
    else if(diffDays<=3){dueClass='due soon';dueLabel=`Due ${fmtDue}`;}
    else{dueClass='due';dueLabel=`Due ${fmtDue}`;}
    dueChip=`<span class="date-chip ${dueClass}">📅 ${dueLabel}</span>`;
  } else if(t.due&&t.status==='done'){
    const dueDate=new Date(t.due+'T00:00:00');
    const fmtDue=dueDate.toLocaleDateString('en-US',{month:'short',day:'numeric'});
    dueChip=`<span class="date-chip due" style="opacity:0.5">📅 ${fmtDue}</span>`;
  }

  let assignHtml='';
  if(isOrphan){
    assignHtml=`<div style="margin-top:10px;display:flex;gap:6px;flex-wrap:wrap">
      <span style="font-size:11px;color:var(--muted);padding-top:5px">Assign:</span>
      <button onclick="assignTask('${t.id}','Pastor Andy')" style="font-size:11px;padding:4px 10px;border-radius:20px;border:1px solid var(--border);background:var(--person-Andy-bg);color:var(--person-Andy);cursor:pointer;font-family:'DM Sans',sans-serif">Pastor Andy</button>
      <button onclick="assignTask('${t.id}','Kaitlyn')"    style="font-size:11px;padding:4px 10px;border-radius:20px;border:1px solid var(--border);background:var(--person-Kaitlyn-bg);color:var(--person-Kaitlyn);cursor:pointer;font-family:'DM Sans',sans-serif">Kaitlyn</button>
      <button onclick="assignTask('${t.id}','Angie')"      style="font-size:11px;padding:4px 10px;border-radius:20px;border:1px solid var(--border);background:var(--person-Angie-bg);color:var(--person-Angie);cursor:pointer;font-family:'DM Sans',sans-serif">Angie</button>
    </div>`;
  }

  // Comments & unread
  const comments=t.comments||[];
  const SHOW=3;
  const unreadCount=getUnreadCount(t);
  const showAll=comments.length<=SHOW;
  const visibleComments=showAll?comments:comments.slice(-SHOW);
  const hiddenCount=comments.length-SHOW;
  const lastRead=readLog[t.id]||0;

  function fmtCommentTime(ts){
    const d=new Date(ts);
    return d.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'})+' at '+d.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});
  }

  const commentsHtml=visibleComments.map(c=>{
    const isUnread=c.ts>lastRead;
    return `<div class="comment-item${isUnread?' unread':''}">
      <div class="comment-dot"></div>
      <div class="comment-body">
        <div class="comment-text">${esc(c.text)}</div>
        <div class="comment-meta">
          ${c.author?`<span class="comment-author">${esc(c.author)}</span> · `:''}
          <span class="comment-datetime">${fmtCommentTime(c.ts)}</span>
        </div>
      </div>
    </div>`;
  }).join('');

  const unreadBadge=unreadCount>0?`<span class="unread-badge">${unreadCount} new</span>`:'';

  // has-unread class on card
  if(unreadCount>0) d.classList.add('has-unread');

  d.innerHTML=`<div class="task-card-top">
    <div class="task-name">${esc(t.name)}</div>
    <button class="delete-btn" onclick="deleteTask('${t.id}')">×</button>
  </div>
  <div class="task-meta">
    <span class="cat-badge cat-${t.cat}">${catObj.label}</span>
    ${ownerHtml}
    <span class="timestamp">${timeAgo(t.ts)}</span>
  </div>
  <div class="date-row">${ageChip}${dueChip}</div>
  <div class="status-toggle">
    <button class="status-btn ${t.status==='not'?'active-not':''}" onclick="setStatus('${t.id}','not')">Not Started</button>
    <button class="status-btn ${t.status==='prog'?'active-prog':''}" onclick="setStatus('${t.id}','prog')">In Progress</button>
    <button class="status-btn ${t.status==='done'?'active-done':''}" onclick="setStatus('${t.id}','done')">Complete</button>
  </div>
  ${assignHtml}
  <div class="notes-section">
    <div class="notes-label">Notes</div>
    <div class="notes-display" id="nd-${t.id}" onclick="editNotes('${t.id}')">${t.notes?esc(t.notes):'<span style="opacity:0.45">Tap to add a note...</span>'}</div>
    <textarea class="notes-edit" id="ne-${t.id}" placeholder="Add a note..."></textarea>
    <div class="notes-edit-actions" id="nea-${t.id}">
      <button class="notes-save-btn" onclick="saveNotes('${t.id}')">Save</button>
      <button class="notes-cancel-btn" onclick="cancelNotes('${t.id}')">Cancel</button>
    </div>
  </div>
  <div class="comments-section" id="cs-${t.id}">
    <div class="notes-label">
      Updates${comments.length>0?' ('+comments.length+')':''}
      ${unreadBadge}
    </div>
    ${!showAll?`<button class="expand-btn" onclick="expandComments('${t.id}')">Show ${hiddenCount} earlier update${hiddenCount!==1?'s':''}</button>`:''}
    <div id="cl-${t.id}">${commentsHtml}</div>
    <div class="comment-input-wrap">
      <div class="comment-author-row">
        <span class="comment-author-label">From:</span>
        <select class="comment-author-select" id="ca-${t.id}">
          <option value="">— Select your name —</option>
          <option value="Pastor Andy">Pastor Andy</option>
          <option value="Kaitlyn">Kaitlyn</option>
          <option value="Angie">Angie</option>
        </select>
      </div>
      <div class="comment-input-row">
        <textarea class="comment-input" id="ci-${t.id}" placeholder="Type an update..." rows="2" onkeydown="if(event.key==='Enter'&&!event.shiftKey){event.preventDefault();submitComment('${t.id}')}"></textarea>
        <button class="comment-submit" onclick="submitComment('${t.id}')">Post</button>
      </div>
    </div>
  </div>`;
  return d;
}

function editNotes(id){
  const display=document.getElementById('nd-'+id);
  const edit=document.getElementById('ne-'+id);
  const actions=document.getElementById('nea-'+id);
  const t=tasks.find(x=>x.id===id);
  if(!t)return;
  edit.value=t.notes||'';
  display.style.display='none';
  edit.style.display='block';
  actions.style.display='flex';
  edit.focus();
}

function cancelNotes(id){
  document.getElementById('nd-'+id).style.display='';
  document.getElementById('ne-'+id).style.display='none';
  document.getElementById('nea-'+id).style.display='none';
}

async function saveNotes(id){
  const t=tasks.find(x=>x.id===id);
  if(!t)return;
  t.notes=document.getElementById('ne-'+id).value.trim();
  t.ts=Date.now();
  cancelNotes(id);
  // update display without full re-render
  const display=document.getElementById('nd-'+id);
  if(display) display.innerHTML=t.notes?esc(t.notes):'<span style="opacity:0.45">Tap to add a note...</span>';
  await pushTasks();
  showNotif('Note saved');
}

async function submitComment(id){
  const input=document.getElementById('ci-'+id);
  const authorSel=document.getElementById('ca-'+id);
  const text=input.value.trim();
  const author=authorSel?authorSel.value:'';
  if(!text){input.focus();return;}
  if(!author){if(authorSel)authorSel.style.border='1px solid var(--danger)';showNotif('Please select your name first');return;}
  if(authorSel)authorSel.style.border='';
  const t=tasks.find(x=>x.id===id);
  if(!t)return;
  if(!t.comments)t.comments=[];
  const newComment={text,author,ts:Date.now()};
  t.comments.push(newComment);
  t.ts=Date.now();
  input.value='';
  // mark as read for this device (I just posted it)
  markTaskRead(id);
  // re-render comment list in place
  refreshCommentList(id,t);
  await pushTasks();
  showNotif('Update posted');
}

function refreshCommentList(id,t){
  const cl=document.getElementById('cl-'+id);
  if(!cl)return;
  const comments=t.comments||[];
  const SHOW=3;
  const lastRead=readLog[id]||0;
  const visibleComments=comments.length<=SHOW?comments:comments.slice(-SHOW);
  function fmtCommentTime(ts){
    const d=new Date(ts);
    return d.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'})+' at '+d.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});
  }
  cl.innerHTML=visibleComments.map(c=>{
    const isUnread=c.ts>lastRead;
    return `<div class="comment-item${isUnread?' unread':''}">
      <div class="comment-dot"></div>
      <div class="comment-body">
        <div class="comment-text">${esc(c.text)}</div>
        <div class="comment-meta">
          ${c.author?`<span class="comment-author">${esc(c.author)}</span> · `:''}
          <span class="comment-datetime">${fmtCommentTime(c.ts)}</span>
        </div>
      </div>
    </div>`;
  }).join('');
  // update header label and badge
  const section=document.getElementById('cs-'+id);
  if(section){
    const unreadCount=getUnreadCount(t);
    const label=section.querySelector('.notes-label');
    if(label)label.innerHTML='Updates'+(comments.length>0?' ('+comments.length+')':'')+
      (unreadCount>0?` <span class="unread-badge">${unreadCount} new</span>`:'');
    // update card border
    const card=section.closest('.task-card');
    if(card)card.classList.toggle('has-unread',unreadCount>0);
  }
}

function expandComments(id){
  const t=tasks.find(x=>x.id===id);
  if(!t||!t.comments)return;
  // mark all as read when user expands
  markTaskRead(id);
  const cl=document.getElementById('cl-'+id);
  if(!cl)return;
  function fmtCommentTime(ts){
    const d=new Date(ts);
    return d.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'})+' at '+d.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});
  }
  cl.innerHTML=t.comments.map(c=>`
    <div class="comment-item">
      <div class="comment-dot"></div>
      <div class="comment-body">
        <div class="comment-text">${esc(c.text)}</div>
        <div class="comment-meta">
          ${c.author?`<span class="comment-author">${esc(c.author)}</span> · `:''}
          <span class="comment-datetime">${fmtCommentTime(c.ts)}</span>
        </div>
      </div>
    </div>`).join('');
  const expandBtn=cl.previousElementSibling;
  if(expandBtn&&expandBtn.classList.contains('expand-btn'))expandBtn.remove();
  refreshCommentList(id,t);
}

function renderReport(){
  const sLabel={not:'Not Started',prog:'In Progress',done:'Complete'};
  const sBadge={not:'badge-not',prog:'badge-prog',done:'badge-done'};
  const tot=tasks.length,dn=tasks.filter(t=>t.status==='done').length;
  const pg=tasks.filter(t=>t.status==='prog').length,nt=tasks.filter(t=>t.status==='not').length;
  const pct=tot?Math.round(dn/tot*100):0;
  let h=`<div class="report-section"><h3>Overall Progress</h3>
    <div style="background:var(--surface2);border-radius:20px;height:6px;margin-bottom:14px;overflow:hidden">
      <div style="background:var(--accent);height:100%;width:${pct}%;border-radius:20px;transition:width 0.6s ease"></div></div>
    <div class="report-row"><span class="label">Total tasks</span><strong>${tot}</strong></div>
    <div class="report-row"><span class="label">Complete</span><span class="report-badge badge-done">${dn}</span></div>
    <div class="report-row"><span class="label">In Progress</span><span class="report-badge badge-prog">${pg}</span></div>
    <div class="report-row"><span class="label">Not Started</span><span class="report-badge badge-not">${nt}</span></div></div>`;

  // by person
  h+=`<div class="report-section"><h3>By Team Member</h3>`;
  PEOPLE.forEach(p=>{
    const pt=tasks.filter(t=>p.match(t));
    if(!pt.length){h+=`<div class="report-row"><span>${p.label}</span><span style="font-size:12px;color:var(--muted)">No tasks</span></div>`;return;}
    const pd=pt.filter(t=>t.status==='done').length;
    h+=`<div class="member-block"><div class="member-header">
      <div class="member-avatar-sm" style="background:${p.bg};color:${p.color}">${p.initials}</div>
      <span class="member-name">${p.label}</span><span class="member-count">${pt.length} task${pt.length!==1?'s':''} · ${pd} done</span></div>`;
    pt.forEach(t=>{h+=`<div class="report-row" style="padding-left:36px"><span style="font-size:13px">${esc(t.name)}</span><span class="report-badge ${sBadge[t.status]}">${sLabel[t.status]}</span></div>`;});
    h+=`</div>`;
  });
  h+=`</div>`;

  // by category
  h+=`<div class="report-section"><h3>By Category</h3>`;
  CATS.forEach(c=>{
    const ct=tasks.filter(t=>t.cat===c.key);
    if(!ct.length)return;
    const cd=ct.filter(t=>t.status==='done').length;
    h+=`<div class="report-row"><span>${c.label}</span><span style="font-size:12px;color:var(--muted)">${cd}/${ct.length} done</span></div>`;
  });
  h+=`</div>`;

  // overdue tasks
  const today=new Date(); today.setHours(0,0,0,0);
  const overdue=tasks.filter(t=>t.due&&t.status!=='done'&&new Date(t.due+'T00:00:00')<today);
  if(overdue.length){
    h+=`<div class="report-section"><h3 style="color:var(--danger)">Overdue (${overdue.length})</h3>`;
    overdue.forEach(t=>{
      const diffDays=Math.round((today-new Date(t.due+'T00:00:00'))/86400000);
      h+=`<div class="report-row"><span style="font-size:13px">${esc(t.name)}<span style="font-size:11px;color:var(--muted);margin-left:6px">${t.owner||'Unassigned'}</span></span><span style="font-size:11px;color:var(--danger);font-weight:500">${diffDays}d overdue</span></div>`;
    });
    h+=`</div>`;
  }

  // orphaned
  const orph=tasks.filter(t=>!t.owner||t.owner.trim()==='');
  if(orph.length){
    h+=`<div class="report-section"><h3 style="color:var(--danger)">Orphaned Tasks (${orph.length})</h3>`;
    orph.forEach(t=>{h+=`<div class="report-row"><span style="font-size:13px">${esc(t.name)}</span><span class="report-badge ${sBadge[t.status]}">${sLabel[t.status]}</span></div>`;});
    h+=`</div>`;
  }

  const now=new Date();
  h+=`<div style="text-align:center;font-size:11px;color:var(--muted);padding:8px 0 4px">Generated ${now.toLocaleDateString()} at ${now.toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'})}</div>`;
  document.getElementById('report-content').innerHTML=h;
}

// ── NAV ───────────────────────────────────────────────────────────────────────
function switchTab(tab){
  activeTab=tab;
  ALL_TABS.forEach(k=>{
    const btn=document.getElementById('tab-btn-'+k);
    if(btn)btn.classList.toggle('active',k===tab);
  });
  const isView=!['add','report','agenda','meetings'].includes(tab);
  document.getElementById('tab-view').style.display=isView?'':'none';
  document.getElementById('tab-add').style.display=tab==='add'?'':'none';
  document.getElementById('tab-report').style.display=tab==='report'?'':'none';
  document.getElementById('tab-agenda').style.display=tab==='agenda'?'':'none';
  document.getElementById('tab-meetings').style.display=tab==='meetings'?'':'none';
  if(tab==='report')renderReport();
  else if(tab==='agenda')renderAgendaTab();
  else if(tab==='meetings')renderMeetingsTab();
  else if(isView)renderCurrentView();
}

// ── HELPERS ───────────────────────────────────────────────────────────────────
function showNotif(msg){const b=document.getElementById('notifBadge');document.getElementById('notifText').textContent=msg;b.classList.add('show');clearTimeout(notifTimer);notifTimer=setTimeout(()=>b.classList.remove('show'),3200);}
function showLoading(msg){document.getElementById('loadingMsg').textContent=msg||'Loading...';document.getElementById('loadingOverlay').classList.remove('hidden');}
function hideLoading(){document.getElementById('loadingOverlay').classList.add('hidden');}
function uid(){return Math.random().toString(36).slice(2,9);}
function ini(n){if(!n)return'?';return n.trim().split(' ').map(x=>x[0]).slice(0,2).join('').toUpperCase();}
function timeAgo(ts){const d=Date.now()-ts;if(d<60000)return'just now';if(d<3600000)return Math.floor(d/60000)+'m ago';if(d<86400000)return Math.floor(d/3600000)+'h ago';return Math.floor(d/86400000)+'d ago';}
function esc(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');}

// ── AGENDA & MEETINGS ─────────────────────────────────────────────────────────

function fmtDate(dateStr){
  if(!dateStr)return'';
  const d=new Date(dateStr+'T00:00:00');
  return d.toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric',year:'numeric'});
}

function renderAgendaTab(){
  const sel=document.getElementById('agenda-meeting-select');
  const prev=sel.value;
  sel.innerHTML='<option value="">— Select a meeting —</option>';
  const sorted=[...meetings].sort((a,b)=>b.date.localeCompare(a.date));
  sorted.forEach(m=>{
    const opt=document.createElement('option');
    opt.value=m.id;
    opt.textContent=(m.title||'Meeting')+' · '+fmtDate(m.date);
    sel.appendChild(opt);
  });
  if(prev)sel.value=prev;
  renderAgendaForMeeting();
}

function renderAgendaForMeeting(){
  const sel=document.getElementById('agenda-meeting-select');
  const mid=sel.value;
  const panel=document.getElementById('agenda-items-panel');
  if(!mid){panel.style.display='none';return;}
  panel.style.display='';
  const m=meetings.find(x=>x.id===mid);
  if(!m)return;
  document.getElementById('agenda-meeting-title-display').textContent=m.title||'Meeting';
  document.getElementById('agenda-meeting-date-display').textContent=fmtDate(m.date);
  const list=document.getElementById('agenda-items-list');
  const empty=document.getElementById('agenda-empty');
  const items=m.agendaItems||[];
  if(!items.length){list.innerHTML='';empty.style.display='';return;}
  empty.style.display='none';
  list.innerHTML=items.map((a,i)=>`
    <div class="agenda-item${a.discussed?' discussed':''}" id="ai-${m.id}-${i}">
      <div class="agenda-check${a.discussed?' checked':''}" onclick="toggleAgendaItem('${m.id}',${i})">${a.discussed?'✓':''}</div>
      <div class="agenda-item-body">
        <div class="agenda-item-topic">${esc(a.topic)}</div>
        ${a.details?`<div class="agenda-item-details">${esc(a.details)}</div>`:''}
        <div class="agenda-item-meta">${a.author?'Added by '+esc(a.author)+' · ':''}${timeAgo(a.ts)}</div>
      </div>
    </div>`).join('');
}

function showNewMeetingForm(context){
  const form=document.getElementById('new-meeting-form');
  form.style.display='block';
  form.dataset.context=context;
  document.getElementById('new-meeting-date').value='';
  document.getElementById('new-meeting-title').value='';
}
function hideNewMeetingForm(){document.getElementById('new-meeting-form').style.display='none';}

async function createMeeting(){
  const date=document.getElementById('new-meeting-date').value;
  const title=document.getElementById('new-meeting-title').value.trim()||'Team Meeting';
  if(!date){showNotif('Please pick a date');return;}
  const m={id:uid(),date,title,notes:'',attachments:[],agendaItems:[],ts:Date.now()};
  meetings.push(m);
  hideNewMeetingForm();
  await pushTasks();
  updateTabCounts();
  const context=document.getElementById('new-meeting-form').dataset.context;
  if(context==='meetings'){renderMeetingsTab();}
  else{renderAgendaTab();document.getElementById('agenda-meeting-select').value=m.id;renderAgendaForMeeting();}
  showNotif('Meeting created');
}

function showAddTopicForm(){document.getElementById('add-topic-form').style.display='block';}
function hideAddTopicForm(){document.getElementById('add-topic-form').style.display='none';}

async function addAgendaTopic(){
  const topic=document.getElementById('topic-text').value.trim();
  const author=document.getElementById('topic-author').value;
  if(!topic){document.getElementById('topic-text').focus();return;}
  if(!author){showNotif('Please select your name');return;}
  const mid=document.getElementById('agenda-meeting-select').value;
  const m=meetings.find(x=>x.id===mid);
  if(!m)return;
  if(!m.agendaItems)m.agendaItems=[];
  m.agendaItems.push({topic,details:document.getElementById('topic-details').value.trim(),author,discussed:false,ts:Date.now()});
  document.getElementById('topic-text').value='';
  document.getElementById('topic-details').value='';
  hideAddTopicForm();
  await pushTasks();
  updateTabCounts();
  renderAgendaForMeeting();
  showNotif('Topic added');
}

async function toggleAgendaItem(mid,idx){
  const m=meetings.find(x=>x.id===mid);
  if(!m||!m.agendaItems[idx])return;
  m.agendaItems[idx].discussed=!m.agendaItems[idx].discussed;
  await pushTasks();
  updateTabCounts();
  renderAgendaForMeeting();
}

// ── MEETINGS NOTES ────────────────────────────────────────────────────────────

function renderMeetingsTab(){
  const listEl=document.getElementById('meetings-list');
  const emptyEl=document.getElementById('meetings-empty');
  const sorted=[...meetings].sort((a,b)=>b.date.localeCompare(a.date));
  if(!sorted.length){listEl.innerHTML='';emptyEl.style.display='';return;}
  emptyEl.style.display='none';
  listEl.innerHTML=sorted.map(m=>`
    <div class="meeting-row" onclick="openMeetingDetail('${m.id}')">
      <div>
        <div class="meeting-row-title">${esc(m.title||'Meeting')}</div>
        <div class="meeting-row-meta">${fmtDate(m.date)}${m.attachments&&m.attachments.length?' · '+m.attachments.length+' attachment'+(m.attachments.length!==1?'s':''):''}</div>
      </div>
      <span style="color:var(--muted);font-size:18px">›</span>
    </div>`).join('');
}

function openMeetingDetail(mid){
  activeMeetingId=mid;
  const m=meetings.find(x=>x.id===mid);
  if(!m)return;
  document.getElementById('meetings-list-view').style.display='none';
  document.getElementById('meetings-detail-view').style.display='';
  document.getElementById('detail-meeting-title').textContent=m.title||'Meeting';
  document.getElementById('detail-meeting-date').textContent=fmtDate(m.date);
  document.getElementById('detail-notes-body').value=m.notes||'';
  renderAttachments(m);
  // show cloudinary setup banner if not configured
  const needsSetup=!creds||!creds.cloudinaryCloud||!creds.cloudinaryPreset;
  document.getElementById('cloudinary-setup-banner').style.display=needsSetup?'':'none';
}

function closeMeetingDetail(){
  activeMeetingId=null;
  document.getElementById('meetings-list-view').style.display='';
  document.getElementById('meetings-detail-view').style.display='none';
}

async function saveMeetingNotes(){
  const m=meetings.find(x=>x.id===activeMeetingId);
  if(!m)return;
  m.notes=document.getElementById('detail-notes-body').value;
  await pushTasks();
  showNotif('Notes saved');
}

function renderAttachments(m){
  const list=document.getElementById('detail-attachments');
  const attachments=m.attachments||[];
  list.innerHTML=attachments.map(a=>`
    <a class="attachment-chip" href="${a.url}" target="_blank">
      📄 ${esc(a.name)}
    </a>`).join('');
}

async function handleFileUpload(event){
  const file=event.target.files[0];
  if(!file)return;
  if(!creds||!creds.cloudinaryCloud||!creds.cloudinaryPreset){
    showNotif('Set up Cloudinary in ⚙ Settings first');
    document.getElementById('cloudinary-setup-banner').style.display='';
    return;
  }
  const prog=document.getElementById('upload-progress');
  prog.style.display='';prog.textContent='Uploading '+file.name+'...';
  try{
    const fd=new FormData();
    fd.append('file',file);
    fd.append('upload_preset',creds.cloudinaryPreset);
    const r=await fetch('https://api.cloudinary.com/v1_1/'+creds.cloudinaryCloud+'/auto/upload',{method:'POST',body:fd});
    if(!r.ok)throw new Error('Upload failed');
    const data=await r.json();
    const m=meetings.find(x=>x.id===activeMeetingId);
    if(!m)return;
    if(!m.attachments)m.attachments=[];
    m.attachments.push({name:file.name,url:data.secure_url,ts:Date.now()});
    renderAttachments(m);
    await pushTasks();
    showNotif('File uploaded');
  }catch(e){showNotif('Upload failed — check Cloudinary settings');}
  finally{prog.style.display='none';event.target.value='';}
}

init();
</script>
</body>
</html>

index.html
cozyinflorida 
(cozy1718@gmail.com)
General Info
TypeHTML
Size74 KB
Location
Modified6:37 PM Apr 19
Created6:37 PM Apr 19
Opened by me6:37 PM Apr 19
Sharing

cozyinflorida
Owner
Description
No description
Displaying index.html.
