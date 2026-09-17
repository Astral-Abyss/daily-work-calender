[index.html](https://github.com/user-attachments/files/32342902/index.html)
[Uploading index.html…]()

<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>夜页 · 每日手账</title>
<meta name="theme-color" content="#1d212a">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="夜页手账">
<meta name="description" content="一款温暖治愈的每日手账应用，记录任务、日记、心情与灵感">
<link rel="manifest" href="manifest.json">
<link rel="apple-touch-icon" href="icons/icon-192.png">
<link rel="icon" type="image/png" sizes="192x192" href="icons/icon-192.png">
<link rel="icon" type="image/png" sizes="512x512" href="icons/icon-512.png">
<link rel="stylesheet" href="https://miaoda.feishu.cn/fonts/css2?family=Noto+Serif+SC:wght@400;600;700&family=Noto+Sans+SC:wght@300;400;500;700&display=swap">
<style>
:root{
  --bg:#1d212a; --bg-glow:#282e3a; --card:#272c38; --card-border:#363d4c;
  --ink:#eae6dc; --ink-dim:#a7aebd; --ink-faint:#7c8494;
  --accent:#e8b15c; --accent-strong:#f3cd85; --accent-dim:rgba(232,177,92,.14);
  --blue:#7fa8e8; --green:#7fc8a0; --danger:#e07a6b;
  --serif:'Noto Serif SC','Songti SC','SimSun',serif;
  --sans:'Noto Sans SC','Microsoft YaHei',system-ui,sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{-webkit-text-size-adjust:100%;}
body{
  font-family:var(--sans); color:var(--ink); line-height:1.6;
  background:radial-gradient(1200px 700px at 50% -10%, var(--bg-glow) 0%, var(--bg) 55%);
  min-height:100vh; padding:36px 28px 72px;
}
.wrap{max-width:min(1260px,94vw);margin:0 auto;}

/* ===== 顶部 ===== */
.app-head{display:flex;align-items:center;gap:20px;padding:20px 6px 44px;flex-wrap:wrap;}
.hero-img{width:96px;height:96px;border-radius:20px;object-fit:cover;border:1px solid var(--card-border);box-shadow:0 4px 20px rgba(0,0,0,.35);flex-shrink:0;}
.head-text{display:flex;flex-direction:column;gap:2px;}
.app-title{font-family:var(--serif);font-size:26px;font-weight:700;letter-spacing:2px;}
.app-title .dot{color:var(--accent);}
.app-sub{font-size:12px;color:var(--ink-faint);letter-spacing:1px;}
.today-chip{margin-left:auto;font-size:12px;color:var(--ink-dim);}

/* ===== 月视图 ===== */
.daily-card{position:relative;border-radius:20px;overflow:hidden;border:1px solid var(--card-border);margin-bottom:clamp(24px,2.5vw,40px);height:clamp(200px,19vw,340px);box-shadow:0 10px 32px rgba(0,0,0,.34);}
.daily-img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;}
.daily-mask{position:absolute;inset:0;background:linear-gradient(105deg,rgba(15,18,26,.85) 0%,rgba(15,18,26,.5) 46%,rgba(15,18,26,.12) 72%);}
.daily-body{position:relative;height:100%;display:flex;flex-direction:column;justify-content:flex-end;padding:24px 28px;box-sizing:border-box;padding-right:160px;}
.daily-label{font-size:12px;letter-spacing:3px;color:var(--accent-strong);margin-bottom:8px;}
.daily-quote{font-family:var(--serif);font-size:clamp(19px,1.8vw,26px);line-height:1.8;color:var(--ink);font-weight:600;text-shadow:0 1px 8px rgba(0,0,0,.5);}
.daily-from{font-size:12px;color:var(--ink-dim);margin-top:6px;text-shadow:0 1px 6px rgba(0,0,0,.5);}
.daily-refresh{position:absolute;top:12px;right:12px;z-index:2;background:rgba(20,24,32,.55);border-color:rgba(255,255,255,.28);color:var(--ink-dim);}
.daily-refresh:hover{color:var(--accent-strong);border-color:var(--accent);}
.daily-card.noimg .daily-img{display:none;}
.daily-card.noimg .daily-mask{background:radial-gradient(900px 320px at 18% 0%, #2b3240 0%, #1d212a 62%);}

.month-head{display:flex;align-items:center;gap:12px;margin-bottom:28px;flex-wrap:wrap;}
.month-title{font-family:var(--serif);font-size:clamp(24px,2.4vw,34px);font-weight:600;color:var(--accent-strong);}
.icon-btn{
  display:inline-flex;align-items:center;justify-content:center;
  min-width:46px;height:46px;border-radius:12px;border:1px solid var(--card-border);
  background:var(--card);color:var(--ink-dim);cursor:pointer;transition:border-color .15s,color .15s;
}
.icon-btn:hover{border-color:var(--accent);color:var(--accent-strong);}
.icon-btn svg{width:16px;height:16px;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;}
.add-btn{min-width:clamp(56px,5vw,72px);height:clamp(56px,5vw,72px);border-radius:18px;flex-shrink:0;}
.add-btn svg{width:clamp(20px,1.8vw,26px);height:clamp(20px,1.8vw,26px);}

.spacer{flex:1;}
.text-btn{
  border:1px solid var(--card-border);background:var(--card);color:var(--ink-dim);
  font-family:var(--sans);font-size:14px;height:46px;padding:0 20px;border-radius:12px;cursor:pointer;transition:border-color .15s,color .15s;
}
.text-btn:hover{border-color:var(--accent);color:var(--accent-strong);}
.text-btn.primary{border-color:var(--accent);color:var(--accent);}
.jump-box{display:flex;gap:6px;}
.jump-sel{
  height:46px;border:1px solid var(--card-border);border-radius:12px;background:var(--card);
  color:var(--ink-dim);font-family:var(--sans);font-size:13px;padding:0 8px;outline:none;cursor:pointer;
  transition:border-color .15s,color .15s;
}
.jump-sel:hover,.jump-sel:focus{border-color:var(--accent);color:var(--accent-strong);}

/* 日历 */
.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:12px;}
.week-row{display:grid;grid-template-columns:repeat(7,1fr);gap:12px;margin-bottom:16px;}
.week-cell{font-size:13px;color:var(--ink-faint);text-align:center;padding:6px 0;letter-spacing:1px;}
.day-cell{
  position:relative;min-height:clamp(95px,9.5vw,160px);border:1px solid var(--card-border);border-radius:16px;
  background:var(--card);padding:clamp(10px,1vw,14px) clamp(12px,1.2vw,16px);cursor:pointer;display:flex;flex-direction:column;gap:clamp(8px,0.8vw,12px);
  transition:border-color .15s,transform .1s;
}
.day-cell:hover{border-color:var(--accent);}
.day-cell.empty{background:transparent;border-color:transparent;cursor:default;}
.day-cell.today{border-color:var(--accent);box-shadow:0 0 0 1px var(--accent) inset;}
.day-num{font-size:clamp(15px,1.4vw,19px);color:var(--ink-dim);line-height:1;}
.day-cell.today .day-num{color:var(--accent-strong);font-weight:700;}
.day-cell.weekend .day-num{color:var(--ink-faint);}
.day-cell.muted{opacity:.42;border-style:dashed;background:transparent;}
.day-cell.muted:hover{opacity:.75;}
.day-sub{font-size:12px;color:var(--ink-faint);line-height:1.4;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;min-height:15px;}
.day-sub.fest{color:var(--accent);}
.day-cell.today .day-sub{color:var(--accent-strong);}
.day-cell.today .day-sub.fest{color:var(--accent-strong);font-weight:600;}
.day-dots{display:flex;gap:6px;margin-top:auto;min-height:8px;}
.dot{width:8px;height:8px;border-radius:50%;}
.dot.blue{background:var(--blue);} .dot.amber{background:var(--accent);} .dot.green{background:var(--green);}
.day-preview{font-size:12.5px;color:var(--ink-faint);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.foot-note{margin-top:32px;font-size:12px;color:var(--ink-faint);display:flex;gap:24px;flex-wrap:wrap;align-items:center;}
.foot-note .tip{display:inline-flex;align-items:center;gap:6px;}
.foot-note .backup{margin-left:auto;display:flex;gap:8px;}

/* ===== 日视图 ===== */
.day-head{display:flex;align-items:center;gap:18px;margin-bottom:40px;flex-wrap:wrap;}
.day-title{font-family:var(--serif);font-size:clamp(22px,2.2vw,32px);font-weight:600;}
.day-title .sub{display:block;font-family:var(--sans);font-size:13px;color:var(--ink-faint);font-weight:400;margin-top:2px;}
.day-illu{position:relative;border-radius:20px;overflow:hidden;border:1px solid var(--card-border);height:clamp(220px,21vw,380px);margin-bottom:clamp(28px,3vw,44px);box-shadow:0 10px 28px rgba(0,0,0,.34);}
.day-illu img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;}
.day-illu-mask{position:absolute;inset:0;background:linear-gradient(90deg,rgba(15,18,26,.72) 0%,rgba(15,18,26,.25) 55%,rgba(15,18,26,.05) 100%);}
.day-illu-tag{position:absolute;left:14px;bottom:10px;font-size:12px;letter-spacing:2px;color:var(--ink);background:rgba(20,24,32,.55);padding:4px 10px;border-radius:20px;border:1px solid rgba(255,255,255,.18);}
.day-illu-refresh{position:absolute;top:10px;right:10px;z-index:2;width:32px;height:32px;padding:0;display:flex;align-items:center;justify-content:center;background:rgba(20,24,32,.55);border-color:rgba(255,255,255,.28);color:var(--ink-dim);}
.day-illu-refresh:hover{color:var(--accent-strong);border-color:var(--accent);}
.day-illu-refresh svg{width:16px;height:16px;}
.day-illu.noimg img{display:none;}
.day-illu.noimg{background:radial-gradient(600px 200px at 15% 0%, #2b3240 0%, #1d212a 62%);}
.poem-card{position:relative;display:flex;align-items:center;border-radius:20px;border:1px solid var(--card-border);background:linear-gradient(135deg,#272e3a 0%,#1d212a 72%);padding:clamp(28px,3vw,44px) clamp(32px,3.5vw,48px);margin-bottom:clamp(28px,3vw,44px);min-height:clamp(220px,17vw,320px);overflow:hidden;}
.poem-card::after{content:'';position:absolute;left:-24px;bottom:-30px;width:120px;height:120px;border-radius:50%;border:1px solid rgba(232,177,92,.16);}
.poem-side{display:flex;flex-direction:column;gap:12px;z-index:1;}
.poem-label{font-size:12px;letter-spacing:3px;color:var(--accent-strong);}
.poem-title{font-family:var(--serif);font-size:25px;font-weight:700;color:var(--ink);}
.poem-author{font-size:12px;color:var(--ink-dim);}
.poem-verse{writing-mode:vertical-rl;text-orientation:upright;font-family:var(--serif);font-size:clamp(17px,1.5vw,21px);line-height:2.1;letter-spacing:4px;color:#e8c98a;margin-left:auto;padding-left:clamp(20px,2vw,28px);border-left:1px dashed rgba(232,177,92,.3);max-height:clamp(200px,15vw,300px);}
.poem-refresh{position:absolute;top:18px;right:18px;z-index:2;width:38px;height:38px;padding:0;display:flex;align-items:center;justify-content:center;background:rgba(20,24,32,.55);border-color:rgba(255,255,255,.28);color:var(--ink-dim);}
.poem-refresh:hover{color:var(--accent-strong);border-color:var(--accent);}
.poem-refresh svg{width:18px;height:18px;}

.tabs{display:flex;gap:14px;background:var(--card);border:1px solid var(--card-border);border-radius:20px;padding:12px;width:100%;margin-bottom:24px;}
.tab{
  flex:1;border:none;background:transparent;color:var(--ink-dim);font-family:var(--sans);
  font-size:clamp(15px,1.3vw,18px);line-height:1;padding:clamp(20px,1.8vw,28px) clamp(18px,1.6vw,24px);border-radius:17px;cursor:pointer;display:flex;align-items:center;justify-content:center;gap:clamp(10px,1vw,14px);transition:background .15s,color .15s;
}
.tab svg{width:17px;height:17px;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;flex-shrink:0;}
.tab.active{background:var(--accent-dim);color:var(--accent-strong);}
.panel{display:none;}
.panel.active{display:block;}

/* 清单 */
.add-row{display:flex;gap:16px;margin-bottom:40px;align-items:stretch;}
.add-input{
  flex:1;height:clamp(56px,5vw,72px);border:1px solid var(--card-border);border-radius:18px;background:var(--card);
  color:var(--ink);font-family:var(--sans);font-size:clamp(15px,1.3vw,18px);padding:0 clamp(18px,1.8vw,26px);outline:none;transition:border-color .15s;
}
.add-input:focus{border-color:var(--accent);}
.add-input::placeholder{color:var(--ink-faint);}
.todo-list{list-style:none;}
.todo-item{
  display:flex;align-items:center;gap:clamp(14px,1.4vw,20px);padding:clamp(20px,2vw,30px) clamp(12px,1.2vw,18px);border-bottom:1px dashed var(--card-border);
}
.todo-item:last-child{border-bottom:none;}
.todo-idx{
  font-family:var(--serif);font-size:16px;color:var(--accent);min-width:38px;text-align:right;opacity:.85;
}
.todo-cb{
  appearance:none;-webkit-appearance:none;width:23px;height:23px;border:1.5px solid var(--ink-faint);
  border-radius:6px;cursor:pointer;flex-shrink:0;display:flex;align-items:center;justify-content:center;transition:all .15s;
}
.todo-cb:hover{border-color:var(--accent);}
.todo-cb:checked{background:var(--accent);border-color:var(--accent);}
.todo-cb:checked::after{content:'';width:9px;height:5px;border-left:2px solid #20242e;border-bottom:2px solid #20242e;transform:rotate(-45deg) translateY(-1px);}
.todo-text{flex:1;font-size:clamp(15px,1.3vw,18px);color:var(--ink);word-break:break-word;}
.todo-item.done .todo-text{color:var(--ink-faint);text-decoration:line-through;}
.todo-del{
  border:none;background:transparent;color:var(--ink-faint);cursor:pointer;width:40px;height:40px;
  border-radius:8px;display:flex;align-items:center;justify-content:center;opacity:0;transition:opacity .15s,color .15s;
}
.todo-item:hover .todo-del{opacity:1;}
.todo-del:hover{color:var(--danger);}
.todo-del svg{width:15px;height:15px;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;}
.todo-count{font-size:13px;color:var(--ink-faint);margin-top:18px;}
.todo-group{margin-bottom:8px;}
.todo-group + .todo-group{margin-top:24px;}
.empty-state{display:flex;flex-direction:column;align-items:center;gap:22px;padding:72px 20px!important;border-bottom:none!important;}
.empty-img{width:280px;max-width:72%;border-radius:18px;opacity:.95;}
.empty-text{font-size:13px;color:var(--ink-faint);}
.group-head{
  display:flex;align-items:center;gap:12px;font-size:14px;color:var(--ink-dim);letter-spacing:1.5px;
  padding:30px 8px 20px;border-bottom:1px solid var(--card-border);
}
.group-head::before{content:'';width:3px;height:12px;border-radius:2px;background:var(--accent);flex-shrink:0;}
#doneGroupT .group-head::before{background:var(--green);}
.group-count{font-size:12px;color:var(--ink-faint);margin-left:auto;}

/* 日记 */
.diary-wrap{position:relative;}
.diary-area{
  width:100%;min-height:clamp(380px,34vw,520px);border:1px solid var(--card-border);border-radius:16px;background:var(--card);
  color:var(--ink);font-family:var(--serif);font-size:clamp(15px,1.3vw,18px);line-height:2.2;padding:clamp(20px,2vw,28px) clamp(22px,2.2vw,30px);outline:none;resize:vertical;transition:border-color .15s;
}
.diary-area:focus{border-color:var(--accent);}
.diary-status{font-size:13px;color:var(--ink-faint);margin-top:16px;text-align:right;}
.diary-export{display:flex;gap:12px;margin-top:20px;justify-content:flex-end;flex-wrap:wrap;}

/* 提示 */
.toast{
  position:fixed;left:50%;bottom:34px;transform:translateX(-50%);background:#343b4a;color:var(--ink);
  font-size:13px;padding:10px 18px;border-radius:10px;border:1px solid var(--card-border);
  opacity:0;pointer-events:none;transition:opacity .25s;z-index:99;max-width:86vw;
}
.toast.show{opacity:1;}

/* ===== 响应式 ===== */
@media (max-width:640px){
  body{padding:14px 10px 30px;}
  .app-title{font-size:19px;}
  .hero-img{width:64px;height:64px;border-radius:14px;}
  .daily-card{height:132px;border-radius:14px;}
  .daily-body{padding:12px 14px;padding-right:104px;}
  .daily-quote{font-size:15px;}
  .daily-label{font-size:11px;}
  .today-chip{margin-left:0;width:100%;}
  .empty-img{width:180px;}
  .day-illu{height:128px;border-radius:14px;}
  .poem-card{min-height:156px;padding:14px 16px;}
  .poem-verse{font-size:14px;line-height:1.9;max-height:156px;}
  .poem-title{font-size:16px;}
  .month-title{font-size:21px;}
  .day-cell{min-height:66px;padding:7px 6px;gap:5px;border-radius:10px;}
  .day-num{font-size:14px;}
  .day-preview{display:none;}
  .day-title{font-size:20px;}
  .week-cell{font-size:12px;}
  .icon-btn{min-width:44px;height:44px;}
  .text-btn{height:44px;}
  .jump-sel{height:40px;font-size:15px;}
  .add-input{font-size:16px;}
  .foot-note{flex-direction:column;align-items:flex-start;gap:10px;}
  .foot-note .backup{margin-left:0;}
  .todo-text{font-size:14px;}
  .diary-area{min-height:260px;font-size:16px;}
  .todo-del{opacity:.6;}
}
@media (prefers-reduced-motion:reduce){
  *{transition:none!important;}
}

/* ===== 心情打卡 ===== */
.mood-bar{display:flex;gap:10px;margin-bottom:clamp(20px,2vw,28px);flex-wrap:wrap;align-items:center;}
.mood-label{font-size:13px;color:var(--ink-dim);margin-right:6px;letter-spacing:1px;}
.mood-btn{width:44px;height:44px;border-radius:12px;border:1px solid var(--card-border);background:var(--card);cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:22px;transition:all .15s;opacity:.55;}
.mood-btn:hover{opacity:.9;transform:translateY(-2px);}
.mood-btn.active{opacity:1;border-color:var(--accent);background:rgba(232,177,92,.12);box-shadow:0 0 0 2px rgba(232,177,92,.2);}
.mood-dot{position:absolute;bottom:6px;left:50%;transform:translateX(-50%);width:8px;height:8px;border-radius:50%;}

/* ===== 任务优先级 ===== */
.todo-priority{width:4px;height:60%;border-radius:2px;flex-shrink:0;}
.priority-high{background:#e87272;}
.priority-normal{background:transparent;}
.priority-low{background:#6b7a8f;}
.todo-idx{cursor:pointer;user-select:none;transition:color .15s;}
.todo-idx:hover{color:var(--accent-strong);}

/* ===== 重复任务 ===== */
.todo-repeat{font-size:11px;color:var(--ink-faint);margin-left:6px;cursor:pointer;padding:2px 6px;border-radius:6px;border:1px solid transparent;transition:all .15s;flex-shrink:0;}
.todo-repeat:hover{border-color:var(--card-border);color:var(--ink-dim);}
.todo-repeat.active{color:var(--accent);border-color:var(--accent);background:rgba(232,177,92,.08);}

/* ===== 纪念日 ===== */
.anniv-badge{position:absolute;top:6px;right:8px;font-size:11px;z-index:2;}
.anniv-banner{background:linear-gradient(135deg,rgba(232,90,90,.15),rgba(232,177,92,.1));border:1px solid rgba(232,177,92,.3);border-radius:14px;padding:14px 18px;margin-bottom:clamp(20px,2vw,28px);display:flex;align-items:center;gap:12px;}
.anniv-banner-icon{font-size:24px;flex-shrink:0;}
.anniv-banner-text{flex:1;}
.anniv-banner-title{font-family:var(--serif);font-size:17px;color:var(--ink);font-weight:600;}
.anniv-banner-sub{font-size:12px;color:var(--ink-dim);margin-top:2px;}

/* ===== 统计区域 ===== */
.stats-bar{display:flex;gap:16px;margin-top:24px;flex-wrap:wrap;}
.stat-card{flex:1;min-width:140px;background:var(--card);border:1px solid var(--card-border);border-radius:14px;padding:16px 18px;}
.stat-label{font-size:12px;color:var(--ink-faint);letter-spacing:1px;margin-bottom:8px;}
.stat-value{font-family:var(--serif);font-size:28px;color:var(--accent-strong);font-weight:700;}
.stat-sub{font-size:12px;color:var(--ink-dim);margin-top:4px;}
.stat-bar-bg{height:6px;background:var(--bg);border-radius:3px;margin-top:10px;overflow:hidden;}
.stat-bar-fill{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent-strong));border-radius:3px;transition:width .3s;}

/* ===== 弹窗 ===== */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.6);z-index:100;display:none;align-items:center;justify-content:center;padding:20px;}
.modal-overlay.show{display:flex;}
.modal{background:var(--card);border:1px solid var(--card-border);border-radius:18px;padding:28px;max-width:480px;width:100%;max-height:80vh;overflow-y:auto;box-shadow:0 20px 60px rgba(0,0,0,.5);}
.modal-title{font-family:var(--serif);font-size:22px;color:var(--ink);margin-bottom:20px;display:flex;align-items:center;justify-content:space-between;}
.modal-close{background:none;border:none;color:var(--ink-faint);cursor:pointer;font-size:20px;width:32px;height:32px;border-radius:8px;display:flex;align-items:center;justify-content:center;}
.modal-close:hover{background:var(--bg);color:var(--ink);}
.modal-input{width:100%;height:48px;border:1px solid var(--card-border);border-radius:12px;background:var(--bg);color:var(--ink);font-family:var(--sans);font-size:15px;padding:0 16px;margin-bottom:12px;outline:none;box-sizing:border-box;}
.modal-input:focus{border-color:var(--accent);}
.modal-row{display:flex;gap:10px;margin-bottom:16px;}
.modal-select{flex:1;height:48px;border:1px solid var(--card-border);border-radius:12px;background:var(--bg);color:var(--ink);font-family:var(--sans);font-size:15px;padding:0 12px;outline:none;}
.modal-btn{height:46px;border-radius:12px;border:none;cursor:pointer;font-family:var(--sans);font-size:15px;font-weight:500;transition:all .15s;}
.modal-btn.primary{flex:1;background:var(--accent);color:#1a1d24;}
.modal-btn.primary:hover{background:var(--accent-strong);}
.modal-btn.ghost{background:transparent;color:var(--ink-dim);border:1px solid var(--card-border);padding:0 16px;}
.modal-btn.ghost:hover{color:var(--ink);border-color:var(--ink-faint);}
.anniv-list-item{display:flex;align-items:center;gap:12px;padding:12px 14px;border-radius:12px;border:1px solid var(--card-border);margin-bottom:8px;}
.anniv-list-icon{font-size:20px;flex-shrink:0;}
.anniv-list-info{flex:1;}
.anniv-list-name{font-size:15px;color:var(--ink);}
.anniv-list-date{font-size:12px;color:var(--ink-dim);margin-top:2px;}
.anniv-list-del{background:none;border:none;color:var(--ink-faint);cursor:pointer;width:32px;height:32px;border-radius:8px;display:flex;align-items:center;justify-content:center;}
.anniv-list-del:hover{background:rgba(232,114,114,.1);color:#e87272;}

/* ===== 主题切换 ===== */
:root[data-theme="light"]{
  --bg:#f5f2ec; --bg-glow:#ebe5d8; --card:#ffffff; --card-border:#e0d9cc;
  --ink:#2a2824; --ink-dim:#6b665c; --ink-faint:#9a9488;
  --accent:#c89040; --accent-strong:#a87020; --accent-dim:rgba(200,144,64,.12);
}
:root[data-theme="warm"]{
  --bg:#2a1f1a; --bg-glow:#3a2a20; --card:#33251e; --card-border:#4a3528;
  --ink:#f0e6d8; --ink-dim:#c4b4a0; --ink-faint:#9a8878;
  --accent:#e8a060; --accent-strong:#f0b878; --accent-dim:rgba(232,160,96,.14);
}
.theme-btn{width:36px;height:36px;border-radius:10px;border:1px solid var(--card-border);background:var(--card);cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:16px;transition:all .15s;}
.theme-btn:hover{border-color:var(--accent);transform:scale(1.05);}

/* ===== 总结弹窗 ===== */
.summary-section{margin-bottom:20px;}
.summary-section-title{font-size:13px;color:var(--ink-faint);letter-spacing:1px;margin-bottom:10px;}
.summary-row{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--card-border);font-size:14px;}
.summary-row:last-child{border-bottom:none;}
.summary-label{color:var(--ink-dim);}
.summary-value{font-family:var(--serif);font-weight:600;color:var(--accent-strong);}
.mood-dist{display:flex;gap:8px;margin-top:8px;flex-wrap:wrap;}
.mood-dist-item{display:flex;align-items:center;gap:4px;font-size:12px;color:var(--ink-dim);background:var(--bg);padding:4px 10px;border-radius:8px;}

/* ===== 日记灵感 ===== */
.inspire-box{background:var(--accent-dim);border:1px solid rgba(232,177,92,.25);border-radius:12px;padding:14px 16px;margin-bottom:14px;font-size:14px;color:var(--ink-dim);line-height:1.7;display:none;}
.inspire-box.show{display:block;}
.inspire-tag{display:inline-block;font-size:11px;color:var(--accent);background:rgba(232,177,92,.1);padding:2px 8px;border-radius:6px;margin-bottom:8px;letter-spacing:1px;}

/* ===== 导出图片按钮 ===== */
.export-img-btn{margin-left:8px;}

/* ===== 周视图 ===== */
.week-head{display:flex;align-items:center;gap:12px;margin-bottom:24px;flex-wrap:wrap;}
.week-title{font-family:var(--serif);font-size:clamp(22px,2.2vw,30px);font-weight:600;color:var(--accent-strong);}
.week-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:12px;margin-bottom:28px;}
.week-day{
  position:relative;min-height:clamp(200px,18vw,320px);border:1px solid var(--card-border);border-radius:16px;
  background:var(--card);padding:14px 12px;cursor:pointer;transition:border-color .15s,transform .15s;
  display:flex;flex-direction:column;
}
.week-day:hover{border-color:var(--accent);transform:translateY(-2px);}
.week-day.today{border-color:var(--accent);box-shadow:0 0 0 2px rgba(232,177,92,.2);}
.week-day.other-month{opacity:.4;}
.week-day-num{font-family:var(--serif);font-size:20px;font-weight:600;color:var(--ink);margin-bottom:2px;}
.week-day-wd{font-size:11px;color:var(--ink-faint);margin-bottom:10px;letter-spacing:1px;}
.week-day-mood{font-size:18px;margin-bottom:8px;min-height:22px;}
.week-day-tasks{flex:1;overflow:hidden;}
.week-day-task{font-size:12px;color:var(--ink-dim);padding:3px 0;border-bottom:1px solid rgba(255,255,255,.04);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.week-day-task.done{text-decoration:line-through;color:var(--ink-faint);}
.week-day-task.high{border-left:2px solid #e87272;padding-left:6px;}
.week-day-more{font-size:11px;color:var(--ink-faint);margin-top:4px;}
.week-day-footer{display:flex;justify-content:space-between;align-items:center;margin-top:8px;padding-top:8px;border-top:1px solid var(--card-border);}
.week-day-rate{font-size:11px;color:var(--accent);}
.week-day-diary{font-size:14px;opacity:.6;}
.week-summary-bar{display:flex;gap:16px;margin-bottom:24px;flex-wrap:wrap;}
</style>
<script>(function (global, factory) {
  typeof exports === 'object' && typeof module !== 'undefined' ? factory(exports) :
  typeof define === 'function' && define.amd ? define(['exports'], factory) :
  (global = typeof globalThis !== 'undefined' ? globalThis : global || self, factory(global.solarLunar = {}));
})(this, (function (exports) { 'use strict';

  /**
   * 农历 1900-2100 的润大小信息表
   * @return Array
   */
  var lunarInfo = [0x04bd8, 0x04ae0, 0x0a570, 0x054d5, 0x0d260, 0x0d950, 0x16554, 0x056a0, 0x09ad0, 0x055d2,//1900-1909
    0x04ae0, 0x0a5b6, 0x0a4d0, 0x0d250, 0x1d255, 0x0b540, 0x0d6a0, 0x0ada2, 0x095b0, 0x14977,//1910-1919
    0x04970, 0x0a4b0, 0x0b4b5, 0x06a50, 0x06d40, 0x1ab54, 0x02b60, 0x09570, 0x052f2, 0x04970,//1920-1929
    0x06566, 0x0d4a0, 0x0ea50, 0x06e95, 0x05ad0, 0x02b60, 0x186e3, 0x092e0, 0x1c8d7, 0x0c950,//1930-1939
    0x0d4a0, 0x1d8a6, 0x0b550, 0x056a0, 0x1a5b4, 0x025d0, 0x092d0, 0x0d2b2, 0x0a950, 0x0b557,//1940-1949
    0x06ca0, 0x0b550, 0x15355, 0x04da0, 0x0a5b0, 0x14573, 0x052b0, 0x0a9a8, 0x0e950, 0x06aa0,//1950-1959
    0x0aea6, 0x0ab50, 0x04b60, 0x0aae4, 0x0a570, 0x05260, 0x0f263, 0x0d950, 0x05b57, 0x056a0,//1960-1969
    0x096d0, 0x04dd5, 0x04ad0, 0x0a4d0, 0x0d4d4, 0x0d250, 0x0d558, 0x0b540, 0x0b6a0, 0x195a6,//1970-1979
    0x095b0, 0x049b0, 0x0a974, 0x0a4b0, 0x0b27a, 0x06a50, 0x06d40, 0x0af46, 0x0ab60, 0x09570,//1980-1989
    0x04af5, 0x04970, 0x064b0, 0x074a3, 0x0ea50, 0x06b58, 0x05ac0, 0x0ab60, 0x096d5, 0x092e0,//1990-1999
    0x0c960, 0x0d954, 0x0d4a0, 0x0da50, 0x07552, 0x056a0, 0x0abb7, 0x025d0, 0x092d0, 0x0cab5,//2000-2009
    0x0a950, 0x0b4a0, 0x0baa4, 0x0ad50, 0x055d9, 0x04ba0, 0x0a5b0, 0x15176, 0x052b0, 0x0a930,//2010-2019
    0x07954, 0x06aa0, 0x0ad50, 0x05b52, 0x04b60, 0x0a6e6, 0x0a4e0, 0x0d260, 0x0ea65, 0x0d530,//2020-2029
    0x05aa0, 0x076a3, 0x096d0, 0x04afb, 0x04ad0, 0x0a4d0, 0x1d0b6, 0x0d250, 0x0d520, 0x0dd45,//2030-2039
    0x0b5a0, 0x056d0, 0x055b2, 0x049b0, 0x0a577, 0x0a4b0, 0x0aa50, 0x1b255, 0x06d20, 0x0ada0,//2040-2049
    /**Add By JJonline@JJonline.Cn**/
    0x14b63, 0x09370, 0x049f8, 0x04970, 0x064b0, 0x168a6, 0x0ea50, 0x06b20, 0x1a6c4, 0x0aae0,//2050-2059
    0x092e0, 0x0d2e3, 0x0c960, 0x0d557, 0x0d4a0, 0x0da50, 0x05d55, 0x056a0, 0x0a6d0, 0x055d4,//2060-2069
    0x052d0, 0x0a9b8, 0x0a950, 0x0b4a0, 0x0b6a6, 0x0ad50, 0x055a0, 0x0aba4, 0x0a5b0, 0x052b0,//2070-2079
    0x0b273, 0x06930, 0x07337, 0x06aa0, 0x0ad50, 0x14b55, 0x04b60, 0x0a570, 0x054e4, 0x0d160,//2080-2089
    0x0e968, 0x0d520, 0x0daa0, 0x16aa6, 0x056d0, 0x04ae0, 0x0a9d4, 0x0a4d0, 0x0d150, 0x0f252,//2090-2099
    0x0d520];//2100;

  /**
   * 公历每个月份的天数普通表
   * @Array Of Property
   * @return Number
   */
  var solarMonth = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

  /**
   * 天干地支之天干速查表
   * @Array Of Property trans['甲','乙','丙','丁','戊','己','庚','辛','壬','癸']
   * @return Cn string
   */
  var gan = [
    '\u7532',
    '\u4e59',
    '\u4e19',
    '\u4e01',
    '\u620a',
    '\u5df1',
    '\u5e9a',
    '\u8f9b',
    '\u58ec',
    '\u7678'
  ];

  /**
   * 天干地支之地支速查表
   * @Array Of Property
   * @trans['子','丑','寅','卯','辰','巳','午','未','申','酉','戌','亥']
   * @return Cn string
   */
  var zhi = [
    '\u5b50',
    '\u4e11',
    '\u5bc5',
    '\u536f',
    '\u8fb0',
    '\u5df3',
    '\u5348',
    '\u672a',
    '\u7533',
    '\u9149',
    '\u620c',
    '\u4ea5'
  ];

  /**
   * 天干地支之地支速查表<=>生肖
   * @Array Of Property
   * @trans['鼠','牛','虎','兔','龙','蛇','马','羊','猴','鸡','狗','猪']
   * @return Cn string
   */
  var animals = [
    '\u9f20',
    '\u725b',
    '\u864e',
    '\u5154',
    '\u9f99',
    '\u86c7',
    '\u9a6c',
    '\u7f8a',
    '\u7334',
    '\u9e21',
    '\u72d7',
    '\u732a'
  ];

  /**
   * 24节气速查表
   * @Array Of Property
   * @trans['小寒','大寒','立春','雨水','惊蛰','春分','清明','谷雨','立夏','小满','芒种','夏至','小暑','大暑','立秋','处暑','白露','秋分','寒露','霜降','立冬','小雪','大雪','冬至']
   * @return Cn string
   */
  var lunarTerm = [
    '\u5c0f\u5bd2', '\u5927\u5bd2', '\u7acb\u6625', '\u96e8\u6c34', '\u60ca\u86f0', '\u6625\u5206', '\u6e05\u660e', '\u8c37\u96e8', '\u7acb\u590f', '\u5c0f\u6ee1', '\u8292\u79cd', '\u590f\u81f3', '\u5c0f\u6691', '\u5927\u6691', '\u7acb\u79cb', '\u5904\u6691', '\u767d\u9732', '\u79cb\u5206', '\u5bd2\u9732', '\u971c\u964d', '\u7acb\u51ac', '\u5c0f\u96ea', '\u5927\u96ea', '\u51ac\u81f3'
  ];

  /**
   * 1900-2100各年的24节气日期速查表
   * @Array Of Property
   * @return 0x string For splice
   */
  var lTermInfo = [
    '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e', '97bcf97c3598082c95f8c965cc920f',
    '97bd0b06bdb0722c965ce1cfcc920f', 'b027097bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e',
    '97bcf97c359801ec95f8c965cc920f', '97bd0b06bdb0722c965ce1cfcc920f', 'b027097bd097c36b0b6fc9274c91aa',
    '97b6b97bd19801ec9210c965cc920e', '97bcf97c359801ec95f8c965cc920f', '97bd0b06bdb0722c965ce1cfcc920f',
    'b027097bd097c36b0b6fc9274c91aa', '9778397bd19801ec9210c965cc920e', '97b6b97bd19801ec95f8c965cc920f',
    '97bd09801d98082c95f8e1cfcc920f', '97bd097bd097c36b0b6fc9210c8dc2', '9778397bd197c36c9210c9274c91aa',
    '97b6b97bd19801ec95f8c965cc920e', '97bd09801d98082c95f8e1cfcc920f', '97bd097bd097c36b0b6fc9210c8dc2',
    '9778397bd097c36c9210c9274c91aa', '97b6b97bd19801ec95f8c965cc920e', '97bcf97c3598082c95f8e1cfcc920f',
    '97bd097bd097c36b0b6fc9210c8dc2', '9778397bd097c36c9210c9274c91aa', '97b6b97bd19801ec9210c965cc920e',
    '97bcf97c3598082c95f8c965cc920f', '97bd097bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b97bd19801ec9210c965cc920e', '97bcf97c3598082c95f8c965cc920f', '97bd097bd097c35b0b6fc920fb0722',
    '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e', '97bcf97c359801ec95f8c965cc920f',
    '97bd097bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e',
    '97bcf97c359801ec95f8c965cc920f', '97bd097bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b97bd19801ec9210c965cc920e', '97bcf97c359801ec95f8c965cc920f', '97bd097bd07f595b0b6fc920fb0722',
    '9778397bd097c36b0b6fc9210c8dc2', '9778397bd19801ec9210c9274c920e', '97b6b97bd19801ec95f8c965cc920f',
    '97bd07f5307f595b0b0bc920fb0722', '7f0e397bd097c36b0b6fc9210c8dc2', '9778397bd097c36c9210c9274c920e',
    '97b6b97bd19801ec95f8c965cc920f', '97bd07f5307f595b0b0bc920fb0722', '7f0e397bd097c36b0b6fc9210c8dc2',
    '9778397bd097c36c9210c9274c91aa', '97b6b97bd19801ec9210c965cc920e', '97bd07f1487f595b0b0bc920fb0722',
    '7f0e397bd097c36b0b6fc9210c8dc2', '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e',
    '97bcf7f1487f595b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b97bd19801ec9210c965cc920e', '97bcf7f1487f595b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722',
    '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e', '97bcf7f1487f531b0b0bb0b6fb0722',
    '7f0e397bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa', '97b6b97bd19801ec9210c965cc920e',
    '97bcf7f1487f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b97bd19801ec9210c9274c920e', '97bcf7f0e47f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b0bc920fb0722',
    '9778397bd097c36b0b6fc9210c91aa', '97b6b97bd197c36c9210c9274c920e', '97bcf7f0e47f531b0b0bb0b6fb0722',
    '7f0e397bd07f595b0b0bc920fb0722', '9778397bd097c36b0b6fc9210c8dc2', '9778397bd097c36c9210c9274c920e',
    '97b6b7f0e47f531b0723b0b6fb0722', '7f0e37f5307f595b0b0bc920fb0722', '7f0e397bd097c36b0b6fc9210c8dc2',
    '9778397bd097c36b0b70c9274c91aa', '97b6b7f0e47f531b0723b0b6fb0721', '7f0e37f1487f595b0b0bb0b6fb0722',
    '7f0e397bd097c35b0b6fc9210c8dc2', '9778397bd097c36b0b6fc9274c91aa', '97b6b7f0e47f531b0723b0b6fb0721',
    '7f0e27f1487f595b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722',
    '9778397bd097c36b0b6fc9274c91aa', '97b6b7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722',
    '7f0e397bd097c35b0b6fc920fb0722', '9778397bd097c36b0b6fc9274c91aa', '97b6b7f0e47f531b0723b0b6fb0721',
    '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b0bc920fb0722', '9778397bd097c36b0b6fc9274c91aa',
    '97b6b7f0e47f531b0723b0787b0721', '7f0e27f0e47f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b0bc920fb0722',
    '9778397bd097c36b0b6fc9210c91aa', '97b6b7f0e47f149b0723b0787b0721', '7f0e27f0e47f531b0723b0b6fb0722',
    '7f0e397bd07f595b0b0bc920fb0722', '9778397bd097c36b0b6fc9210c8dc2', '977837f0e37f149b0723b0787b0721',
    '7f07e7f0e47f531b0723b0b6fb0722', '7f0e37f5307f595b0b0bc920fb0722', '7f0e397bd097c35b0b6fc9210c8dc2',
    '977837f0e37f14998082b0787b0721', '7f07e7f0e47f531b0723b0b6fb0721', '7f0e37f1487f595b0b0bb0b6fb0722',
    '7f0e397bd097c35b0b6fc9210c8dc2', '977837f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721',
    '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722', '977837f0e37f14998082b0787b06bd',
    '7f07e7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e397bd097c35b0b6fc920fb0722',
    '977837f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722',
    '7f0e397bd07f595b0b0bc920fb0722', '977837f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721',
    '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b0bc920fb0722', '977837f0e37f14998082b0787b06bd',
    '7f07e7f0e47f149b0723b0787b0721', '7f0e27f0e47f531b0b0bb0b6fb0722', '7f0e397bd07f595b0b0bc920fb0722',
    '977837f0e37f14998082b0723b06bd', '7f07e7f0e37f149b0723b0787b0721', '7f0e27f0e47f531b0723b0b6fb0722',
    '7f0e397bd07f595b0b0bc920fb0722', '977837f0e37f14898082b0723b02d5', '7ec967f0e37f14998082b0787b0721',
    '7f07e7f0e47f531b0723b0b6fb0722', '7f0e37f1487f595b0b0bb0b6fb0722', '7f0e37f0e37f14898082b0723b02d5',
    '7ec967f0e37f14998082b0787b0721', '7f07e7f0e47f531b0723b0b6fb0722', '7f0e37f1487f531b0b0bb0b6fb0722',
    '7f0e37f0e37f14898082b0723b02d5', '7ec967f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721',
    '7f0e37f1487f531b0b0bb0b6fb0722', '7f0e37f0e37f14898082b072297c35', '7ec967f0e37f14998082b0787b06bd',
    '7f07e7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e37f0e37f14898082b072297c35',
    '7ec967f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722',
    '7f0e37f0e366aa89801eb072297c35', '7ec967f0e37f14998082b0787b06bd', '7f07e7f0e47f149b0723b0787b0721',
    '7f0e27f1487f531b0b0bb0b6fb0722', '7f0e37f0e366aa89801eb072297c35', '7ec967f0e37f14998082b0723b06bd',
    '7f07e7f0e47f149b0723b0787b0721', '7f0e27f0e47f531b0723b0b6fb0722', '7f0e37f0e366aa89801eb072297c35',
    '7ec967f0e37f14998082b0723b06bd', '7f07e7f0e37f14998083b0787b0721', '7f0e27f0e47f531b0723b0b6fb0722',
    '7f0e37f0e366aa89801eb072297c35', '7ec967f0e37f14898082b0723b02d5', '7f07e7f0e37f14998082b0787b0721',
    '7f07e7f0e47f531b0723b0b6fb0722', '7f0e36665b66aa89801e9808297c35', '665f67f0e37f14898082b0723b02d5',
    '7ec967f0e37f14998082b0787b0721', '7f07e7f0e47f531b0723b0b6fb0722', '7f0e36665b66a449801e9808297c35',
    '665f67f0e37f14898082b0723b02d5', '7ec967f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721',
    '7f0e36665b66a449801e9808297c35', '665f67f0e37f14898082b072297c35', '7ec967f0e37f14998082b0787b06bd',
    '7f07e7f0e47f531b0723b0b6fb0721', '7f0e26665b66a449801e9808297c35', '665f67f0e37f1489801eb072297c35',
    '7ec967f0e37f14998082b0787b06bd', '7f07e7f0e47f531b0723b0b6fb0721', '7f0e27f1487f531b0b0bb0b6fb0722'
  ];

  /**
   * 数字转中文速查表
   * @Array Of Property
   * @trans ['日','一','二','三','四','五','六','七','八','九','十']
   * @return Cn string
   */
  var nStr1 = [
    '\u65e5',
    '\u4e00',
    '\u4e8c',
    '\u4e09',
    '\u56db',
    '\u4e94',
    '\u516d',
    '\u4e03',
    '\u516b',
    '\u4e5d',
    '\u5341'
  ];

  /**
   * 日期转农历称呼速查表
   * @Array Of Property
   * @trans ['初','十','廿','卅']
   * @return Cn string
   */
  var nStr2 = ['\u521d', '\u5341', '\u5eff', '\u5345'];

  /**
   * 月份转农历称呼速查表
   * @Array Of Property
   * @trans ['正','一','二','三','四','五','六','七','八','九','十','冬','腊']
   * @return Cn string
   */
  var nStr3 = [
    '\u6b63',
    '\u4e8c',
    '\u4e09',
    '\u56db',
    '\u4e94',
    '\u516d',
    '\u4e03',
    '\u516b',
    '\u4e5d',
    '\u5341',
    '\u51ac',
    '\u814a'
  ];

  /**
   * 年份数字转中文速查表
   * @Array Of Property
   * @trans ['零','一','二','三','四','五','六','七','八','九','十']
   * @return Cn string
   */
  var nStr4 = [
    '\u96f6',
    '\u4e00',
    '\u4e8c',
    '\u4e09',
    '\u56db',
    '\u4e94',
    '\u516d',
    '\u4e03',
    '\u516b',
    '\u4e5d',
    '\u5341'
  ];

  /**
   * @1900-2100区间内的公历、农历互转
   * @charset  UTF-8
   * @author  Ajing(JJonline@JJonline.Cn), Modernized by OpenCode
   * @Time  2014-7-21
   * @Version  $ID$
   * @公历转农历：solarLunar.solar2lunar(1987,11,01); //[you can ignore params of prefix 0]
   * @农历转公历：solarLunar.lunar2solar(1987,09,10); //[you can ignore params of prefix 0]
   * @link http://blog.jjonline.cn/userInterFace/173.html
   */


  const solarLunar = {
    lunarInfo,
    solarMonth,
    gan,
    zhi,
    animals,
    lunarTerm,
    lTermInfo,
    nStr1,
    nStr2,
    nStr3,
    nStr4,

    /**
     * 返回农历y年一整年的总天数
     * @param {number} y - lunar Year
     * @returns {number}
     * @eg:var count = solarLunar.lYearDays(1987) ;//count=387
     */
    lYearDays(y) {
      let sum = 348;
      const info = lunarInfo[y - 1900];
      // 优化：直接计算位数，减少循环
      sum += info & 0x8000 ? 1 : 0;
      sum += info & 0x4000 ? 1 : 0;
      sum += info & 0x2000 ? 1 : 0;
      sum += info & 0x1000 ? 1 : 0;
      sum += info & 0x0800 ? 1 : 0;
      sum += info & 0x0400 ? 1 : 0;
      sum += info & 0x0200 ? 1 : 0;
      sum += info & 0x0100 ? 1 : 0;
      sum += info & 0x0080 ? 1 : 0;
      sum += info & 0x0040 ? 1 : 0;
      sum += info & 0x0020 ? 1 : 0;
      sum += info & 0x0010 ? 1 : 0;
      return sum + solarLunar.leapDays(y);
    },

    /**
     * 返回农历y年闰月是哪个月；若y年没有闰月 则返回0
     * @param {number} y - lunar Year
     * @returns {number} (0-12)
     * @eg:var leapMonth = solarLunar.leapMonth(1987) ;//leapMonth=6
     */
    leapMonth(y) {
      //闰字编码 \u95f0
      return lunarInfo[y - 1900] & 0xf;
    },

    /**
     * 返回农历y年闰月的天数 若该年没有闰月则返回0
     * @param {number} y - lunar Year
     * @returns {number} (0、29、30)
     * @eg:var leapMonthDay = solarLunar.leapDays(1987) ;//leapMonthDay=29
     */
    leapDays(y) {
      if (solarLunar.leapMonth(y)) {
        return lunarInfo[y - 1900] & 0x10000 ? 30 : 29;
      }
      return 0;
    },

    /**
     * 返回农历 y 年 m 月（非闰月）的总天数，计算 m 为闰月时的天数请使用 leapDays 方法
     * @param {number} y - lunar Year
     * @param {number} m - lunar Month
     * @returns {number} (-1、29、30)
     * @eg:var MonthDay = solarLunar.monthDays(1987,9) ;//MonthDay=29
     */
    monthDays(y, m) {
      if (m > 12 || m < 1) {
        return -1;
      } //月份参数从1至12，参数错误返回-1
      return lunarInfo[y - 1900] & (0x10000 >> m) ? 30 : 29;
    },

    /**
     * 获取时辰干支
     * @param {number} h - 公历小时 (0-23)
     * @param {number} dayGanIndex - 日干索引 (0-9)，0=甲，1=乙，...，9=癸
     * @returns {string} 时辰干支，如 "甲子"
     * @eg:var shichen = solarLunar.getShiChen(23, 0); // 23:00 的子时，日干为甲时
     */
    getShiChen(h, dayGanIndex) {
      const hourZhiIndex = (h + 1) / 2 >= 24 ? 0 : Math.floor((h + 1) / 2) % 12;
      const hourGanIndex = (dayGanIndex * 2 + hourZhiIndex) % 10;
      return gan[hourGanIndex] + zhi[hourZhiIndex];
    },

    /**
     * 返回公历(!)y年m月的天数
     * @param {number} y - solar Year
     * @param {number} m - solar Month
     * @returns {number} (-1、28、29、30、31)
     * @eg:var solarMonthDay = solarLunar.solarDays(1987) ;//solarMonthDay=30
     */
    solarDays(y, m) {
      if (m > 12 || m < 1) {
        return -1;
      } //若参数错误 返回-1
      const ms = m - 1;
      if (ms === 1) {
        //2月份的闰平规律测算后确认返回28或29
        return (y % 4 === 0 && y % 100 !== 0) || y % 400 === 0 ? 29 : 28;
      } else {
        return solarMonth[ms];
      }
    },

    /**
     * 传入offset偏移量返回干支
     * @param {number} offset - 相对甲子的偏移量
     * @returns {string} Cn string
     */
    toGanZhi(offset) {
      return gan[offset % 10] + zhi[offset % 12];
    },

    /**
     * 传入公历(!) y 年获得该年第 n 个节气的公历日期
     * @param {number} y - 公历年(1900-2100)；n二十四节气中的第几个节气(1~24)；从n=1(小寒)算起
     * @param {number} n - 二十四节气中的第几个节气(1~24)
     * @returns {number}
     * @eg:var _24 = solarLunar.getTerm(1987,3) ;//_24=4;意即1987年2月4日立春
     */
    getTerm(y, n) {
      if (y < 1900 || y > 2100) {
        return -1;
      }
      if (n < 1 || n > 24) {
        return -1;
      }
      const _table = lTermInfo[y - 1900];
      const _info = [
        parseInt('0x' + _table.substr(0, 5)).toString(),
        parseInt('0x' + _table.substr(5, 5)).toString(),
        parseInt('0x' + _table.substr(10, 5)).toString(),
        parseInt('0x' + _table.substr(15, 5)).toString(),
        parseInt('0x' + _table.substr(20, 5)).toString(),
        parseInt('0x' + _table.substr(25, 5)).toString(),
      ];
      const _calDay = [
        _info[0].substr(0, 1),
        _info[0].substr(1, 2),
        _info[0].substr(3, 1),
        _info[0].substr(4, 2),

        _info[1].substr(0, 1),
        _info[1].substr(1, 2),
        _info[1].substr(3, 1),
        _info[1].substr(4, 2),

        _info[2].substr(0, 1),
        _info[2].substr(1, 2),
        _info[2].substr(3, 1),
        _info[2].substr(4, 2),

        _info[3].substr(0, 1),
        _info[3].substr(1, 2),
        _info[3].substr(3, 1),
        _info[3].substr(4, 2),

        _info[4].substr(0, 1),
        _info[4].substr(1, 2),
        _info[4].substr(3, 1),
        _info[4].substr(4, 2),

        _info[5].substr(0, 1),
        _info[5].substr(1, 2),
        _info[5].substr(3, 1),
        _info[5].substr(4, 2),
      ];
      return parseInt(_calDay[n - 1]);
    },

    /**
     * 传入农历年份数字返回汉语通俗表示法
     * @param {number} y - lunar year
     * @returns {string}
     * @eg:
     */
    toChinaYear(y) {
      //年 => \u5E74
      const oxxx = Math.floor(y / 1000);
      const xoxx = Math.floor((y % 1000) / 100);
      const xxox = Math.floor((y % 100) / 10);
      const xxxo = y % 10;

      return nStr4[oxxx] + nStr4[xoxx] + nStr4[xxox] + nStr4[xxxo] + '\u5E74';
    },

    /**
     * 传入农历数字月份返回汉语通俗表示法
     * @param {number} m - lunar month
     * @returns {string}
     * @eg:var cnMonth = solarLunar.toChinaMonth(12) ;//cnMonth='腊月'
     */
    toChinaMonth(m) {
      // 月 => \u6708
      if (m > 12 || m < 1) {
        return -1;
      } //若参数错误 返回-1
      let s = nStr3[m - 1];
      s += '\u6708'; //加上月字
      return s;
    },

    /**
     * 传入农历日期数字返回汉字表示法
     * @param {number} d - lunar day
     * @returns {string} Cn string
     * @eg:var cnDay = solarLunar.toChinaDay(21) ;//cnMonth='廿一'
     */
    toChinaDay(d) {
      //日 => \u65e5
      let s = '';
      switch (d) {
      case 10:
        s = '\u521d\u5341';
        break;
      case 20:
        s = '\u4e8c\u5341';
        break;
      case 30:
        s = '\u4e09\u5341';
        break;
      default:
        s = nStr2[Math.floor(d / 10)];
        s += nStr1[d % 10];
      }
      return s;
    },

    /**
     * 年份转生肖 => 精确划分生肖分界线是"立春"
     * @param {number} y - year
     * @param {number} [m] - month (可选，用于精确计算)
     * @param {number} [d] - day (可选，用于精确计算)
     * @returns {string} Cn string
     * @eg:var animal = solarLunar.getAnimal(1987) ;//animal='兔'
     */
    getAnimal(y, m, d) {
      // 如果提供了月日参数，基于立春进行精确计算
      if (m !== undefined && d !== undefined) {
        const term3 = solarLunar.getTerm(y, 3); // 立春日期
        // 如果日期在立春之前，则生肖按上一年计算
        if (m < 2 || (m === 2 && d < term3)) {
          y = y - 1;
        }
      }
      return animals[(y - 4) % 12];
    },

    /**
     * 传入公历年月日获得详细的公历、农历object信息 <=>JSON
     * @param {number} y - solar year
     * @param {number} m - solar month
     * @param {number} d - solar day
     * @returns {object} JSON object
     * @eg:console.log(solarLunar.solar2lunar(1987,11,01));
     */
    solar2lunar(y, m, d) {
      //参数区间1900.1.31~2100.12.31
      // 输入验证
      if (y == null || m == null || d == null) {
        const objDate = new Date();
        y = objDate.getFullYear();
        m = objDate.getMonth() + 1;
        d = objDate.getDate();
      }

      // 类型转换和验证
      y = Number(y);
      m = Number(m);
      d = Number(d);

      if (isNaN(y) || isNaN(m) || isNaN(d)) {
        return -1;
      }

      if (y < 1900 || y > 2100) {
        return -1;
      } //年份限定、上限
      if (y === 1900 && m === 1 && d < 31) {
        return -1;
      } //下限

      // 验证月份和日期的有效性
      if (m < 1 || m > 12) {
        return -1;
      }
      const maxDay = solarLunar.solarDays(y, m);
      if (d < 1 || d > maxDay) {
        return -1;
      }

      const objDate = new Date(y, parseInt(m) - 1, d);
      let i,
        temp = 0;
      //修正ymd参数
      y = objDate.getFullYear();
      m = objDate.getMonth() + 1;
      d = objDate.getDate();
      let offset =
        (Date.UTC(objDate.getFullYear(), objDate.getMonth(), objDate.getDate()) -
          Date.UTC(1900, 0, 31)) /
        86400000;

      // 使用原有的线性搜索算法以保持兼容性，但修复变量重声明问题
      temp = 0;
      for (i = 1900; i < 2101 && offset > 0; i++) {
        temp = solarLunar.lYearDays(i);
        offset -= temp;
      }
      if (offset < 0) {
        offset += temp;
        i--;
      }

      const finalYear = i;

      //是否今天
      const isTodayObj = new Date();
      let isToday = false;
      if (
        isTodayObj.getFullYear() === y &&
        isTodayObj.getMonth() + 1 === m &&
        isTodayObj.getDate() === d
      ) {
        isToday = true;
      }
      //星期几
      const nWeek = objDate.getDay();
      const cWeek = nStr1[nWeek];
      const nWeekAdjusted = nWeek === 0 ? 7 : nWeek; //数字表示周几顺应天朝周一开始的惯例

      //农历年
      const year = finalYear;

      const leapMonth = solarLunar.leapMonth(finalYear); //闰哪个月

      let isLeap = false;

      //效验闰月
      for (i = 1; i < 13 && offset > 0; i++) {
        //闰月
        if (leapMonth > 0 && i === leapMonth + 1 && isLeap === false) {
          --i;
          isLeap = true;
          temp = solarLunar.leapDays(year); //计算农历闰月天数
        } else {
          temp = solarLunar.monthDays(year, i); //计算农历普通月天数
        }
        //解除闰月
        if (isLeap === true && i === leapMonth + 1) {
          isLeap = false;
        }
        offset -= temp;
      }

      if (offset === 0 && leapMonth > 0 && i === leapMonth + 1) {
        if (isLeap) {
          isLeap = false;
        } else {
          isLeap = true;
          --i;
        }
      }
      if (offset < 0) {
        offset += temp;
        --i;
      }
      //农历月
      const month = i;
      //农历日
      const day = offset + 1;

      //天干地支处理
      // 注意：干支年以立春为分界线，这是中国传统历法
      // 立春通常在2月3-5日之间，立春之前出生的人，干支属上一年
      const sm = m - 1;
      const term3 = solarLunar.getTerm(y, 3); //该公历年立春日期
      let gzY = solarLunar.toGanZhi(y - 4); //普通按年份计算，下方尚需按立春节气来修正
      //依据立春日进行修正gzY
      // 立春通常在2月3-5日之间，如果日期早于立春，应按上一年计算
      if (m < 2 || (m === 2 && d < term3)) {
        gzY = solarLunar.toGanZhi(y - 1 - 4);
      }

      //月柱 1900年1月小寒以前为 丙子月(60进制12)
      const firstNode = solarLunar.getTerm(y, m * 2 - 1); //返回当月「节」为几日开始
      const secondNode = solarLunar.getTerm(y, m * 2); //返回当月「节」为几日开始

      //依据12节气修正干支月
      // 使用原始的正确算法：年干支索引*12 + 月份 + 偏移
      let gzM = solarLunar.toGanZhi((y - 1900) * 12 + m + 11);
      if (d >= firstNode) {
        gzM = solarLunar.toGanZhi((y - 1900) * 12 + m + 12);
      }

      //传入的日期的节气与否
      let isTerm = false;
      let term = '';
      if (firstNode === d) {
        isTerm = true;
        term = lunarTerm[m * 2 - 2];
      }
      if (secondNode === d) {
        isTerm = true;
        term = lunarTerm[m * 2 - 1];
      }
      //日柱 当月一日与 1900/1/1 相差天数
      const dayCyclical = Date.UTC(y, sm, 1, 0, 0, 0, 0) / 86400000 + 25567 + 10;
      const gzD = solarLunar.toGanZhi(dayCyclical + d - 1);
      return {
        lYear: year,
        lMonth: month,
        lDay: day,
        animal: solarLunar.getAnimal(year),
        yearCn: solarLunar.toChinaYear(year),
        monthCn: (isLeap && leapMonth === month ? '\u95f0' : '') + solarLunar.toChinaMonth(month),
        dayCn: solarLunar.toChinaDay(day),
        cYear: y,
        cMonth: m,
        cDay: d,
        gzYear: gzY,
        gzMonth: gzM,
        gzDay: gzD,
        isToday,
        isLeap,
        nWeek: nWeekAdjusted, //数字表示周几顺应天朝周一开始的惯例
        ncWeek: '\u661f\u671f' + cWeek,
        isTerm,
        term,
      };
    },

    /**
     * 传入公历年月日以及传入的月份是否闰月获得详细的公历、农历object信息 <=>JSON
     * @param {number} y - lunar year
     * @param {number} m - lunar month
     * @param {number} d - lunar day
     * @param {boolean} isLeapMonth - lunar month is leap or not.
     * @returns {object} JSON object
     * @eg:console.log(solarLunar.lunar2solar(1987,9,10));
     */
    lunar2solar(y, m, d, isLeapMonth) {
      //参数区间1900.1.31~2100.12.1
      // 输入验证
      y = Number(y);
      m = Number(m);
      d = Number(d);
      isLeapMonth = Boolean(isLeapMonth); // 确保是布尔值

      if (isNaN(y) || isNaN(m) || isNaN(d)) {
        return -1;
      }
      const leapMonth = solarLunar.leapMonth(y);
      if (isLeapMonth && leapMonth !== m) {
        return -1;
      } //传参要求计算该闰月公历 但该年得出的闰月与传参的月份并不同
      if ((y === 2100 && m === 12 && d > 1) || (y === 1900 && m === 1 && d < 31)) {
        return -1;
      } //超出了最大极限值
      const day = solarLunar.monthDays(y, m);
      if (y < 1900 || y > 2100 || d > day) {
        return -1;
      } //参数合法性效验

      //计算农历的时间差
      let offset = 0;
      for (let i = 1900; i < y; i++) {
        offset += solarLunar.lYearDays(i);
      }
      let leap = 0,
        isAdd = false;
      for (let i = 1; i < m; i++) {
        leap = solarLunar.leapMonth(y);
        if (!isAdd) {
          //处理闰月
          if (leap <= i && leap > 0) {
            offset += solarLunar.leapDays(y);
            isAdd = true;
          }
        }
        offset += solarLunar.monthDays(y, i);
      }
      //转换闰月农历 需补充该年闰月的前一个月的时差
      if (isLeapMonth) {
        offset += day;
      }
      //1900年农历正月一日的公历时间为1900年1月30日0时0分0秒(该时间也是本农历的最开始起始点)
      const stmap = Date.UTC(1900, 1, 30, 0, 0, 0);
      const calObj = new Date((offset + d - 31) * 86400000 + stmap);
      const cY = calObj.getUTCFullYear();
      const cM = calObj.getUTCMonth() + 1;
      const cD = calObj.getUTCDate();

      return solarLunar.solar2lunar(cY, cM, cD);
    },

    /**
     * 获取指定日期的传统节日
     * @param {number} year - 公历年
     * @param {number} month - 公历月
     * @param {number} day - 公历日
     * @returns {string[]} 传统节日数组
     */
    getFestivals(year, month, day) {
      const festivals = [];
      const lunar = solarLunar.solar2lunar(year, month, day);
      if (lunar === -1) return festivals;

      const { lMonth, lDay } = lunar;

      const fixedFestivals = {
        '1-1': '春节',
        '1-15': '元宵节',
        '5-5': '端午节',
        '7-7': '七夕节',
        '8-15': '中秋节',
        '9-9': '重阳节',
        '12-8': '腊八节',
        '12-23': '小年',
      };

      const key = `${lMonth}-${lDay}`;
      if (fixedFestivals[key]) {
        festivals.push(fixedFestivals[key]);
      }

      if (lMonth === 1 && lDay === 1) {
        festivals.push('农历新年');
      }

      if (solarLunar.customFestivals) {
        solarLunar.customFestivals.forEach((f) => {
          if (f.month === lMonth && f.day === lDay) {
            festivals.push(f.name);
          }
        });
      }

      return festivals;
    },

    /**
     * 添加自定义农历节日
     * @param {string} name - 节日名称
     * @param {number} month - 农历月
     * @param {number} day - 农历日
     */
    addFestival(name, month, day) {
      if (!solarLunar.customFestivals) {
        solarLunar.customFestivals = [];
      }
      solarLunar.customFestivals.push({ name, month, day });
    },

    /**
     * 清除所有自定义节日
     */
    clearFestivals() {
      solarLunar.customFestivals = [];
    },
  };

  exports.default = solarLunar;

  Object.defineProperty(exports, '__esModule', { value: true });

}));
//# sourceMappingURL=solarlunar.min.js.map
</script>
<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
</head>
<body>
<div class="wrap">

  <!-- ===== 顶部 ===== -->
  <header class="app-head">
    <img class="hero-img" src="data:image/webp;base64,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" alt="夜页插画">
    <div class="head-text">
      <div class="app-title">夜页<span class="dot">·</span>每日手账</div>
      <div class="app-sub">清单 · 日记 · 明日规划</div>
    </div>
    <div class="today-chip" id="todayChip"></div>
    <button class="theme-btn" data-action="cycle-theme" title="切换主题" id="themeBtn">🌙</button>
  </header>

  <!-- ===== 视图：月 ===== -->
  <section id="monthView">
  <!-- ===== 每日一图 + 语录 ===== -->
  <section class="daily-card" id="dailyCard">
    <img class="daily-img" id="dailyImg" alt="每日插图">
    <div class="daily-mask"></div>
    <div class="daily-body">
      <div class="daily-label">今日插图 · 励志语录</div>
      <div class="daily-quote" id="dailyQuote">正在摘取今日语录…</div>
      <div class="daily-from" id="dailyFrom"></div>
    </div>
    <button class="daily-refresh icon-btn" data-action="refresh-daily" aria-label="换一条" title="换一条">
      <svg viewBox="0 0 24 24"><path d="M21 12a9 9 0 11-2.6-6.4M21 3v6h-6"/></svg>
    </button>
  </section>

    <div class="month-head">
      <button class="icon-btn" data-action="prev-month" aria-label="上个月" id="btnPrev">
        <svg viewBox="0 0 24 24"><path d="M15 18l-6-6 6-6"/></svg>
      </button>
      <div class="month-title" id="monthTitle"></div>
      <button class="icon-btn" data-action="next-month" aria-label="下个月" id="btnNext">
        <svg viewBox="0 0 24 24"><path d="M9 6l6 6-6 6"/></svg>
      </button>
      <div class="spacer"></div>
      <div class="jump-box">
        <button class="text-btn" data-action="view-week" title="切换到周视图">周视图</button>
        <select id="yearSel" class="jump-sel" aria-label="选择年份"></select>
        <select id="monthSel" class="jump-sel" aria-label="选择月份"></select>
      </div>
      <button class="text-btn primary" data-action="goto-today">回到今天</button>
    </div>
    <div class="week-row" id="weekRow"></div>
    <div class="cal-grid" id="calGrid"></div>
    <div class="stats-bar" id="statsBar">
      <div class="stat-card">
        <div class="stat-label">本月完成率</div>
        <div class="stat-value" id="statRate">0%</div>
        <div class="stat-bar-bg"><div class="stat-bar-fill" id="statRateBar" style="width:0%"></div></div>
      </div>
      <div class="stat-card">
        <div class="stat-label">连续打卡</div>
        <div class="stat-value" id="statStreak">0 天</div>
        <div class="stat-sub" id="statStreakSub">坚持记录，每天进步一点点</div>
      </div>
      <div class="stat-card">
        <div class="stat-label">本月任务</div>
        <div class="stat-value" id="statTasks">0/0</div>
        <div class="stat-sub" id="statTasksSub">已完成 / 总计</div>
      </div>
    </div>
    <div class="foot-note">
      <span class="tip"><span class="dot blue"></span>今日清单</span>
      <span class="tip"><span class="dot amber"></span>日记</span>
      <span class="tip"><span class="dot green"></span>明日计划</span>
      <span class="backup">
        <button class="text-btn" data-action="week-summary">本周总结</button>
        <button class="text-btn" data-action="month-summary">本月总结</button>
        <button class="text-btn" data-action="data-stats">数据统计</button>
        <button class="text-btn" data-action="manage-anniv">纪念日</button>
        <button class="text-btn" data-action="export-all">备份数据</button>
        <button class="text-btn" data-action="import-all">导入备份</button>
      </span>
    </div>
  </section>

  <!-- ===== 视图：周 ===== -->
  <section id="weekView" style="display:none;">
    <div class="week-head">
      <button class="icon-btn" data-action="prev-week" aria-label="上一周">
        <svg viewBox="0 0 24 24"><path d="M15 18l-6-6 6-6"/></svg>
      </button>
      <div class="week-title" id="weekTitle"></div>
      <button class="icon-btn" data-action="next-week" aria-label="下一周">
        <svg viewBox="0 0 24 24"><path d="M9 6l6 6-6 6"/></svg>
      </button>
      <div class="spacer"></div>
      <button class="text-btn" data-action="view-month" title="切换到月视图">月视图</button>
      <button class="text-btn primary" data-action="goto-today-week">回到本周</button>
    </div>
    <div class="week-summary-bar" id="weekSummaryBar"></div>
    <div class="week-grid" id="weekGrid"></div>
  </section>

  <!-- ===== 视图：日 ===== -->
  <section id="dayView" style="display:none;">
    <div class="day-head">
      <button class="icon-btn" data-action="back" aria-label="返回日历" id="btnBack">
        <svg viewBox="0 0 24 24"><path d="M19 12H5M12 19l-7-7 7-7"/></svg>
      </button>
      <button class="icon-btn" data-action="prev-day" aria-label="前一天" id="btnPrevDay">
        <svg viewBox="0 0 24 24"><path d="M15 18l-6-6 6-6"/></svg>
      </button>
      <div class="day-title" id="dayTitle"></div>
      <button class="icon-btn" data-action="next-day" aria-label="后一天" id="btnNextDay">
        <svg viewBox="0 0 24 24"><path d="M9 6l6 6-6 6"/></svg>
      </button>
    </div>
    <div class="day-illu" id="dayIllu">
      <img id="dayIlluImg" alt="每日插图">
      <div class="day-illu-mask"></div>
      <div class="day-illu-tag" id="dayIlluTag">每日一图</div>
      <button class="day-illu-refresh icon-btn" data-action="refresh-day-illu" aria-label="换一张插图" title="换一张插图">
        <svg viewBox="0 0 24 24"><path d="M21 12a9 9 0 11-2.6-6.4M21 3v6h-6"/></svg>
      </button>
    </div>
    <div id="annivBanner"></div>
    <div class="mood-bar" id="moodBar">
      <span class="mood-label">今日心情</span>
      <button class="mood-btn" data-mood="happy" title="开心">😊</button>
      <button class="mood-btn" data-mood="calm" title="平静">😌</button>
      <button class="mood-btn" data-mood="tired" title="疲惫">😴</button>
      <button class="mood-btn" data-mood="sad" title="难过">😢</button>
      <button class="mood-btn" data-mood="angry" title="生气">😠</button>
      <button class="mood-btn" data-mood="excited" title="兴奋">🤩</button>
    </div>
    <div class="poem-card" id="quoteCard">
      <div class="poem-side">
        <div class="poem-label">今日励志</div>
        <div class="poem-title" id="quoteTitle">动漫台词</div>
        <div class="poem-author" id="quoteAuthor">—— 蒙奇·D·路飞</div>
      </div>
      <div class="poem-verse" id="quoteVerse">我可是要成为海贼王的男人！</div>
      <button class="poem-refresh icon-btn" data-action="refresh-quote" aria-label="换一条语录" title="换一条语录">
        <svg viewBox="0 0 24 24"><path d="M21 12a9 9 0 11-2.6-6.4M21 3v6h-6"/></svg>
      </button>
    </div>
    <div class="tabs">
      <button class="tab" data-action="set-tab" data-tab="t" id="tabT">
        <svg viewBox="0 0 24 24"><path d="M4 6h16M4 12h16M4 18h10"/></svg>今日清单
      </button>
      <button class="tab" data-action="set-tab" data-tab="d" id="tabD">
        <svg viewBox="0 0 24 24"><path d="M12 20h9M16.5 3.5a2.1 2.1 0 013 3L7 19l-4 1 1-4z"/></svg>日记
      </button>
      <button class="tab" data-action="set-tab" data-tab="p" id="tabP">
        <svg viewBox="0 0 24 24"><path d="M5 12h14M13 6l6 6-6 6"/></svg>明日计划
      </button>
    </div>

    <!-- 清单面板 -->
    <div class="panel" id="panelT">
      <div class="add-row">
        <input class="add-input" id="inputT" placeholder="记录今天做的一件事，回车添加" autocomplete="off">
        <button class="icon-btn add-btn" data-action="add-todo" data-list="t" aria-label="添加" id="btnAddT">
          <svg viewBox="0 0 24 24"><path d="M12 5v14M5 12h14"/></svg>
        </button>
      </div>
      <div class="todo-group">
        <div class="group-head">待完成 <span class="group-count" id="countT"></span></div>
        <ul class="todo-list" id="listT"></ul>
      </div>
      <div class="todo-group" id="doneGroupT" style="display:none;">
        <div class="group-head">今日已做 <span class="group-count" id="countDoneT"></span></div>
        <ul class="todo-list" id="listDoneT"></ul>
      </div>
    </div>

    <!-- 日记面板 -->
    <div class="panel" id="panelD">
      <div class="diary-wrap">
        <textarea class="diary-area" id="diaryArea" placeholder="今天过得怎么样？写下想说的话……"></textarea>
      </div>
      <div class="diary-status" id="diaryStatus"></div>
      <div class="inspire-box" id="inspireBox">
        <span class="inspire-tag">写作灵感</span>
        <div id="inspireText"></div>
      </div>
      <div class="diary-export" style="display:flex;gap:10px;flex-wrap:wrap;">
        <button class="text-btn" data-action="inspire">给我灵感</button>
        <button class="text-btn" data-action="export-day">导出当日为文本</button>
        <button class="text-btn" data-action="export-img">导出手账图片</button>
      </div>
    </div>

    <!-- 计划面板 -->
    <div class="panel" id="panelP">
      <div class="add-row">
        <input class="add-input" id="inputP" placeholder="写下明天要做的一件事，回车添加" autocomplete="off">
        <button class="icon-btn add-btn" data-action="add-todo" data-list="p" aria-label="添加" id="btnAddP">
          <svg viewBox="0 0 24 24"><path d="M12 5v14M5 12h14"/></svg>
        </button>
      </div>
      <ul class="todo-list" id="listP"></ul>
      <div class="todo-count" id="countP"></div>
    </div>
  </section>

</div>
<div class="toast" id="toast"></div>

<input type="file" id="importFile" accept=".json" style="display:none;">

<script>
(function(){
'use strict';

/* ===== 数据层 ===== */
var STORE_KEY='nightpages_v1';
var DB={};
function load(){ try{ return JSON.parse(localStorage.getItem(STORE_KEY))||{}; }catch(e){ return {}; } }
function persist(){ try{ localStorage.setItem(STORE_KEY, JSON.stringify(DB)); }catch(e){ toast('保存失败：浏览器存储不可用'); } }
function getDay(k){ if(!DB[k]) DB[k]={t:[],d:'',p:[],mood:null}; return DB[k]; }
function dayKey(d){ return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0'); }
function todayKey(){ return dayKey(new Date()); }
function parseKey(k){ var a=k.split('-'); return new Date(+a[0],+a[1]-1,+a[2]); }
function fmtCN(k){
  var d=parseKey(k);
  var w=['日','一','二','三','四','五','六'][d.getDay()];
  return d.getFullYear()+'年'+(d.getMonth()+1)+'月'+d.getDate()+'日 星期'+w;
}
function hasAny(k){ var g=DB[k]; if(!g) return {t:false,d:false,p:false}; return {t:!!(g.t&&g.t.length),d:!!(g.d&&g.d.trim()),p:!!(g.p&&g.p.length)}; }

/* ===== 心情配置 ===== */
var MOODS={happy:{icon:'😊',name:'开心',color:'#f0c040'},calm:{icon:'😌',name:'平静',color:'#7ab8d4'},tired:{icon:'😴',name:'疲惫',color:'#8a7fb8'},sad:{icon:'😢',name:'难过',color:'#6b9bd4'},angry:{icon:'😠',name:'生气',color:'#d47070'},excited:{icon:'🤩',name:'兴奋',color:'#e89050'}};

/* ===== 纪念日 ===== */
function getAnnivs(){ if(!DB._annivs) DB._annivs=[]; return DB._annivs; }
function addAnniv(name,date,type){
  var list=getAnnivs();
  list.push({id:Date.now()+''+Math.floor(Math.random()*999),name:name,date:date,type:type||'other'});
  persist();
}
function delAnniv(id){
  DB._annivs=getAnnivs().filter(function(x){return x.id!==id;});
  persist();
}
function getAnnivsOfDate(dateKey){
  var parts=dateKey.split('-'); var mmdd=parts[1]+'-'+parts[2];
  return getAnnivs().filter(function(x){return x.date.slice(5)===mmdd;});
}
function annivIcon(type){ return type==='birthday'?'🎂':type==='anniversary'?'💝':'📌'; }

/* ===== 连续打卡 ===== */
function markActive(dateKey){
  if(!DB._streak) DB._streak={count:0,last:null};
  var s=DB._streak;
  if(s.last===dateKey) return;
  if(s.last){
    var last=parseKey(s.last); var cur=parseKey(dateKey);
    var diff=Math.round((cur-last)/86400000);
    if(diff===1){ s.count++; }
    else if(diff>1){ s.count=1; }
  }else{ s.count=1; }
  s.last=dateKey;
  persist();
}
function getStreak(){ return (DB._streak&&DB._streak.count)||0; }

/* ===== 主题切换 ===== */
var THEMES=['dark','light','warm'];
var THEME_ICONS={dark:'🌙',light:'☀️',warm:'🔥'};
function getTheme(){ try{ return localStorage.getItem('nightpages_theme')||'dark'; }catch(e){ return 'dark'; } }
function setTheme(t){
  try{ localStorage.setItem('nightpages_theme',t); }catch(e){}
  if(t==='dark'){ document.documentElement.removeAttribute('data-theme'); }
  else{ document.documentElement.setAttribute('data-theme',t); }
  var btn=document.getElementById('themeBtn');
  if(btn) btn.textContent=THEME_ICONS[t]||'🌙';
}
function cycleTheme(){
  var cur=getTheme(); var idx=THEMES.indexOf(cur);
  var next=THEMES[(idx+1)%THEMES.length];
  setTheme(next);
  toast('主题：'+(next==='dark'?'深夜':next==='light'?'日间':'暖光'));
}

/* ===== 日记灵感库 ===== */
var INSPIRATIONS=[
  '今天最让你开心的一件小事是什么？',
  '如果今天可以重来，你会做什么不同的选择？',
  '记录一个今天遇到的陌生人，他/她给你留下了什么印象？',
  '今天的天气如何？它影响了你的心情吗？',
  '写下今天学到的一个新知识或新技能。',
  '今天有没有哪一刻让你感到时间变慢了？',
  '描述今天吃的最美味的一顿饭。',
  '今天有没有想起某个很久没联系的人？为什么？',
  '写下今天的一个小目标，以及你是否完成了它。',
  '今天的你和昨天的你有什么不同？',
  '记录一个今天听到的有趣的对话或句子。',
  '如果用一首歌形容今天，会是哪首？为什么？',
  '今天有没有什么让你感到感恩的事？',
  '描述今天看到的最美的一个画面。',
  '今天有没有克服一个小困难？是怎么做到的？',
  '写下对明天的一个期待。',
  '今天的精力状态如何？什么消耗了你，什么补充了你？',
  '记录一个今天突然冒出的想法或灵感。',
  '如果给今天打个分（1-10），你会打几分？为什么？',
  '今天有没有做什么让自己骄傲的事？'
];
function showInspiration(){
  var text=INSPIRATIONS[Math.floor(Math.random()*INSPIRATIONS.length)];
  document.getElementById('inspireText').textContent=text;
  document.getElementById('inspireBox').classList.add('show');
}

/* ===== 周/月总结 ===== */
function buildSummary(startDate,endDate,title){
  var total=0,done=0,diaryDays=0,moodCount={};
  var cur=new Date(startDate);
  while(cur<=endDate){
    var k=dayKey(cur);
    var g=DB[k];
    if(g){
      if(g.t){ total+=g.t.length; done+=g.t.filter(function(x){return x.done;}).length; }
      if(g.d&&g.d.trim()) diaryDays++;
      if(g.mood){ moodCount[g.mood]=(moodCount[g.mood]||0)+1; }
    }
    cur.setDate(cur.getDate()+1);
  }
  var rate=total?Math.round(done/total*100):0;
  var days=Math.round((endDate-startDate)/86400000)+1;
  var html='<div class="summary-section"><div class="summary-section-title">概览</div>';
  html+='<div class="summary-row"><span class="summary-label">统计天数</span><span class="summary-value">'+days+' 天</span></div>';
  html+='<div class="summary-row"><span class="summary-label">任务总数</span><span class="summary-value">'+total+' 项</span></div>';
  html+='<div class="summary-row"><span class="summary-label">已完成</span><span class="summary-value">'+done+' 项</span></div>';
  html+='<div class="summary-row"><span class="summary-label">完成率</span><span class="summary-value">'+rate+'%</span></div>';
  html+='<div class="summary-row"><span class="summary-label">写日记天数</span><span class="summary-value">'+diaryDays+' 天</span></div>';
  html+='</div>';
  // 心情分布
  var moodEntries=Object.entries(moodCount).sort(function(a,b){return b[1]-a[1];});
  if(moodEntries.length){
    html+='<div class="summary-section"><div class="summary-section-title">心情分布</div><div class="mood-dist">';
    moodEntries.forEach(function(m){
      html+='<span class="mood-dist-item">'+MOODS[m[0]].icon+' '+MOODS[m[0]].name+' '+m[1]+'天</span>';
    });
    html+='</div></div>';
  }
  // 鼓励语
  var encourage='';
  if(rate>=80) encourage='太棒了！这段时间效率很高，继续保持！';
  else if(rate>=50) encourage='不错的表现，还有提升空间，加油！';
  else if(total>0) encourage='任务完成率还有提升空间，试着把大任务拆小，一步步来。';
  else encourage='这段时间还没有记录任务，从明天开始试着记录吧。';
  html+='<div class="summary-section"><div class="summary-section-title">小结</div><div style="font-size:14px;color:var(--ink-dim);line-height:1.8;">'+encourage+'</div></div>';
  document.getElementById('summaryTitle').textContent=title;
  document.getElementById('summaryContent').innerHTML=html;
  document.getElementById('summaryModal').classList.add('show');
}
function weekSummary(){
  var today=new Date();
  var day=today.getDay()||7; // 周一为1
  var monday=new Date(today); monday.setDate(today.getDate()-day+1);
  var sunday=new Date(monday); sunday.setDate(monday.getDate()+6);
  buildSummary(monday,sunday,'本周总结');
}
function monthSummary(){
  var today=new Date();
  var first=new Date(today.getFullYear(),today.getMonth(),1);
  var last=new Date(today.getFullYear(),today.getMonth()+1,0);
  buildSummary(first,last,'本月总结');
}

/* ===== 数据统计 ===== */
function showDataStats(){
  var totalDays=0,totalTasks=0,doneTasks=0,totalDiaryChars=0,moodCount={};
  Object.keys(DB).forEach(function(k){
    if(k.indexOf('_')===0) return;
    var g=DB[k];
    if(!g) return;
    var hasContent=false;
    if(g.t&&g.t.length){ totalTasks+=g.t.length; doneTasks+=g.t.filter(function(x){return x.done;}).length; hasContent=true; }
    if(g.d&&g.d.trim()){ totalDiaryChars+=g.d.length; hasContent=true; }
    if(g.mood){ moodCount[g.mood]=(moodCount[g.mood]||0)+1; hasContent=true; }
    if(hasContent) totalDays++;
  });
  var rate=totalTasks?Math.round(doneTasks/totalTasks*100):0;
  var html='<div class="summary-section"><div class="summary-section-title">总览</div>';
  html+='<div class="summary-row"><span class="summary-label">记录天数</span><span class="summary-value">'+totalDays+' 天</span></div>';
  html+='<div class="summary-row"><span class="summary-label">任务总数</span><span class="summary-value">'+totalTasks+' 项</span></div>';
  html+='<div class="summary-row"><span class="summary-label">已完成</span><span class="summary-value">'+doneTasks+' 项</span></div>';
  html+='<div class="summary-row"><span class="summary-label">总完成率</span><span class="summary-value">'+rate+'%</span></div>';
  html+='<div class="summary-row"><span class="summary-label">日记总字数</span><span class="summary-value">'+totalDiaryChars+' 字</span></div>';
  html+='</div>';
  // 心情分布
  var moodEntries=Object.entries(moodCount).sort(function(a,b){return b[1]-a[1];});
  if(moodEntries.length){
    html+='<div class="summary-section"><div class="summary-section-title">心情分布</div><div class="mood-dist">';
    moodEntries.forEach(function(m){
      html+='<span class="mood-dist-item">'+MOODS[m[0]].icon+' '+MOODS[m[0]].name+' '+m[1]+'天</span>';
    });
    html+='</div></div>';
  }
  html+='<div class="summary-section"><div class="summary-section-title">数据管理</div>';
  html+='<div style="display:flex;gap:10px;flex-wrap:wrap;">';
  html+='<button class="modal-btn ghost" data-action="export-all">导出备份</button>';
  html+='<button class="modal-btn ghost" style="color:#e87272;border-color:rgba(232,114,114,.3);" data-action="clear-all">清空所有数据</button>';
  html+='</div></div>';
  document.getElementById('summaryTitle').textContent='数据统计';
  document.getElementById('summaryContent').innerHTML=html;
  document.getElementById('summaryModal').classList.add('show');
}
function clearAllData(){
  if(!confirm('确定要清空所有数据吗？此操作不可恢复！建议先导出备份。')) return;
  DB={};
  try{ localStorage.removeItem(STORE_KEY); }catch(e){}
  document.getElementById('summaryModal').classList.remove('show');
  render();
  toast('所有数据已清空');
}


/* ===== 导出手账图片 ===== */
function exportHandbookImage(){
  var target=document.getElementById('dayView');
  if(!target){ toast('请先进入日视图'); return; }
  toast('正在生成图片，请稍候…');
  // 临时隐藏不需要的元素
  var hidden=[];
  document.querySelectorAll('.icon-btn,.text-btn,.theme-btn,.add-btn,.todo-del,.mood-btn,.daily-refresh,.day-illu-refresh').forEach(function(el){
    if(el.offsetParent!==null){ el.style.visibility='hidden'; hidden.push(el); }
  });
  setTimeout(function(){
    html2canvas(target,{
      backgroundColor:null,
      scale:2,
      useCORS:true,
      allowTaint:true
    }).then(function(canvas){
      hidden.forEach(function(el){ el.style.visibility=''; });
      var link=document.createElement('a');
      link.download='夜页手账_'+state.day+'.png';
      link.href=canvas.toDataURL('image/png');
      link.click();
      toast('图片已保存到下载文件夹');
    }).catch(function(){
      hidden.forEach(function(el){ el.style.visibility=''; });
      toast('导出失败，请重试');
    });
  },300);
}


/* ===== 重复任务处理 ===== */
function processRepeatTasks(){
  var tk=todayKey();
  var today=parseKey(tk);
  var processedKeys={};
  // 遍历所有日期，检查重复任务
  Object.keys(DB).forEach(function(k){
    if(k.indexOf('_')===0) return;
    var g=DB[k];
    if(!g||!g.t) return;
    g.t.forEach(function(it){
      if(!it.repeat||it.repeat==='none'||!it.repeatFrom) return;
      var repeatKey=it.repeatFrom+'_'+it.text;
      if(processedKeys[repeatKey]) return;
      processedKeys[repeatKey]=true;
      // 计算应该生成的日期
      var from=parseKey(it.repeatFrom);
      var days=Math.round((today-from)/86400000);
      if(days<0) return;
      for(var d=1;d<=days;d++){
        var dt=new Date(from.getTime()+d*86400000);
        var dk=dayKey(dt);
        var shouldGen=false;
        if(it.repeat==='daily') shouldGen=true;
        else if(it.repeat==='weekly') shouldGen=(dt.getDay()===from.getDay());
        else if(it.repeat==='monthly') shouldGen=(dt.getDate()===from.getDate());
        if(shouldGen){
          var dg=getDay(dk);
          var exists=dg.t.some(function(x){return x.text===it.text&&x.repeatFrom===it.repeatFrom;});
          if(!exists){
            dg.t.push({id:Date.now()+''+Math.floor(Math.random()*999),text:it.text,done:false,priority:it.priority||'normal',repeat:it.repeat,repeatFrom:it.repeatFrom});
          }
        }
      }
    });
  });
  persist();
}


/* ===== 插画素材 ===== */
var EMPTY_IMG='data:image/webp;base64,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';

/* ===== 农历 / 节日 ===== */
var LIB=(window.solarLunar&&window.solarLunar.default)||window.solarLunar||null;
var SOLAR_FEST={
  '1-1':'元旦','2-14':'情人节','3-8':'妇女节','3-12':'植树节','4-1':'愚人节',
  '5-1':'劳动节','5-4':'青年节','6-1':'儿童节','7-1':'建党节','8-1':'建军节',
  '9-10':'教师节','10-1':'国庆节','11-11':'光棍节','12-24':'平安夜','12-25':'圣诞节'
};
function daySub(y,m,d){
  if(!LIB) return '';
  var sf=SOLAR_FEST[m+'-'+d];
  if(sf) return {t:sf,f:true};
  var info=LIB.solar2lunar(y,m,d);
  if(info===-1||!info) return '';
  try{
    var fes=LIB.getFestivals(y,m,d);
    if(fes&&fes.length) return {t:fes[0],f:true};
  }catch(e){}
  if(info.isTerm&&info.term) return {t:info.term,f:false};
  if(info.dayCn==='初一') return {t:info.monthCn,f:false};
  return {t:info.dayCn,f:false};
}

/* ===== 路由状态 ===== */
var state={ view:'month', month:null, week:null, day:null, tab:'t' };
function initMonth(){ var d=new Date(); state.month=d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0'); }
function parseHash(){
  var h=location.hash||'';
  var m=h.match(/^#\/day\/(\d{4}-\d{2}-\d{2})(?:\/([tdp]))?/);
  if(m){ state.view='day'; state.day=m[1]; state.tab=m[2]||'t'; return; }
  m=h.match(/^#\/week\/(\d{4}-\d{2}-\d{2})/);
  if(m){ state.view='week'; state.week=m[1]; return; }
  m=h.match(/^#\/(\d{4}-\d{2})/);
  if(m){ state.view='month'; state.month=m[1]; return; }
  state.view='month'; if(!state.month) initMonth();
}
function setHash(){
  if(state.view==='day') location.hash='#/day/'+state.day+'/'+state.tab;
  else if(state.view==='week') location.hash='#/week/'+state.week;
  else location.hash='#/'+state.month;
}
window.addEventListener('hashchange',function(){ parseHash(); render(); });

/* ===== 工具 ===== */
var toastTimer=null;
function toast(msg){
  var el=document.getElementById('toast'); el.textContent=msg; el.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ el.classList.remove('show'); },2200);
}
function esc(s){ return String(s).replace(/[&<>"']/g,function(c){return {'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c];}); }
function svgCheck(){ return '<svg viewBox="0 0 24 24" style="width:10px;height:10px;fill:none;stroke:currentColor;stroke-width:3;stroke-linecap:round;stroke-linejoin:round;"><path d="M20 6L9 17l-5-5"/></svg>'; }

/* ===== 渲染：月 ===== */
function renderMonth(){
  document.getElementById('monthView').style.display='block';
  document.getElementById('dayView').style.display='none';
  var parts=state.month.split('-'); var y=+parts[0], m=+parts[1];
  document.getElementById('monthTitle').textContent=y+'年'+m+'月';
  var ys=document.getElementById('yearSel'), ms=document.getElementById('monthSel');
  if(ys&&ms){ ys.value=String(y); ms.value=String(m); }

  var week=['一','二','三','四','五','六','日'];
  document.getElementById('weekRow').innerHTML=week.map(function(w){return '<div class="week-cell">'+w+'</div>';}).join('');

  var first=new Date(y,m-1,1);
  var lead=(first.getDay()+6)%7;            // 周一起始偏移
  var days=new Date(y,m,0).getDate();       // 本月天数
  var total=Math.ceil((lead+days)/7)*7;     // 铺满整行，含相邻月
  var tk=todayKey();
  var html='';
  for(var i=0;i<total;i++){
    var offset=i-lead;
    var cur=new Date(y,m-1,1+offset);
    var yy=cur.getFullYear(), mm=cur.getMonth()+1, dd=cur.getDate();
    var key=dayKey(cur);
    var inMonth=(offset>=0&&offset<days);
    var cls=['day-cell'];
    if(!inMonth) cls.push('muted');
    if(key===tk) cls.push('today');
    var dow=cur.getDay();
    if(dow===0||dow===6) cls.push('weekend');
    var has=hasAny(key);
    var dots='';
    if(has.t) dots+='<span class="dot blue"></span>';
    if(has.d) dots+='<span class="dot amber"></span>';
    if(has.p) dots+='<span class="dot green"></span>';
    // 心情颜色
    var moodHtml='';
    var g=DB[key];
    if(g&&g.mood&&MOODS[g.mood]){
      moodHtml='<span class="mood-dot" style="background:'+MOODS[g.mood].color+'"></span>';
    }
    // 纪念日标记
    var annivHtml='';
    if(inMonth){
      var annivs=getAnnivsOfDate(key);
      if(annivs.length){ annivHtml='<span class="anniv-badge">'+annivIcon(annivs[0].type)+'</span>'; }
    }
    var sub='';
    if(inMonth&&LIB){
      var si=daySub(yy,mm,dd);
      if(si) sub='<div class="day-sub'+(si.f?' fest':'')+'">'+esc(si.t)+'</div>';
    }
    var prev='';
    var g=DB[key];
    if(g){
      var pend=(g.t||[]).filter(function(x){return !x.done;});
      if(g.t&&g.t.length&&!pend.length) prev='<div class="day-preview" style="color:var(--green);">已全部完成</div>';
      else if(pend.length) prev='<div class="day-preview">'+esc(pend[0].text)+'</div>';
      else if(g.d&&g.d.trim()) prev='<div class="day-preview">'+esc(g.d.trim().slice(0,10))+'…</div>';
      else if(g.p&&g.p.length) prev='<div class="day-preview">明日：'+esc(g.p[0].text)+'</div>';
    }
    html+='<div class="'+cls.join(' ')+'" data-action="'+(inMonth?'open-day':'open-month')+'" data-date="'+key+'">'+
      annivHtml+'<div class="day-num">'+dd+'</div>'+sub+'<div class="day-dots">'+dots+'</div>'+moodHtml+prev+'</div>';
  }
  document.getElementById('calGrid').innerHTML=html;
  document.getElementById('todayChip').textContent=fmtCN(tk);
  // 计算本月统计
  var totalT=0,doneT=0;
  for(var di=1;di<=days;di++){
    var dk=y+'-'+String(m).padStart(2,'0')+'-'+String(di).padStart(2,'0');
    var dg=DB[dk];
    if(dg&&dg.t){
      totalT+=dg.t.length;
      doneT+=dg.t.filter(function(x){return x.done;}).length;
    }
  }
  var rate=totalT?Math.round(doneT/totalT*100):0;
  document.getElementById('statRate').textContent=rate+'%';
  document.getElementById('statRateBar').style.width=rate+'%';
  document.getElementById('statStreak').textContent=getStreak()+' 天';
  document.getElementById('statTasks').textContent=doneT+'/'+totalT;
  renderDaily();
}

/* ===== 渲染：日 ===== */

/* ===== 每日励志语录库 ===== */
var QUOTES = [
  {t:"动漫台词", q:"我可是要成为海贼王的男人！", a:"蒙奇·D·路飞《海贼王》"},
  {t:"动漫台词", q:"不能保护同伴的人，不配当忍者。", a:"漩涡鸣人《火影忍者》"},
  {t:"动漫台词", q:"人类的赞歌就是勇气的赞歌！", a:"威廉·A·齐贝林《JOJO》"},
  {t:"动漫台词", q:"只要有树叶飞舞的地方，火就会燃烧。", a:"三代火影《火影忍者》"},
  {t:"动漫台词", q:"我会连她那份一起变强的。", a:"炭治郎《鬼灭之刃》"},
  {t:"动漫台词", q:"无论多少次，我都会站起来。", a:"孙悟空《龙珠》"},
  {t:"动漫台词", q:"不要回头，时代在前进。", a:"空条承太郎《JOJO》"},
  {t:"动漫台词", q:"我要成为火影，这就是我的忍道！", a:"漩涡鸣人《火影忍者》"},
  {t:"动漫台词", q:"燃烧吧！我的小宇宙！", a:"星矢《圣斗士星矢》"},
  {t:"动漫台词", q:"我要成为世界第一的大剑豪！", a:"罗罗诺亚·索隆《海贼王》"},
  {t:"动漫台词", q:"人的梦想，是不会终结的！", a:"马歇尔·D·蒂奇《海贼王》"},
  {t:"动漫台词", q:"把我的心脏献上！", a:"调查兵团《进击的巨人》"},
  {t:"动漫台词", q:"我要把所有巨人都驱逐出去！", a:"艾伦《进击的巨人》"},
  {t:"动漫台词", q:"真正的胜利，是坚持到最后。", a:"星矢《圣斗士星矢》"},
  {t:"动漫台词", q:"不要逃避，活下去！", a:"《海贼王》"},
  {t:"名人名言", q:"只有意志坚强的人，才能到达彼岸。", a:"马克思"},
  {t:"名人名言", q:"唯有勇气，才是永恒。", a:"丘吉尔"},
  {t:"名人名言", q:"不要等待机会，而要创造机会。", a:"萧伯纳"},
  {t:"名人名言", q:"每次跌倒后，都能爬起来。", a:"曼德拉"},
  {t:"名人名言", q:"星光不问赶路人，时光不负有心人。", a:"佚名"},
  {t:"名人名言", q:"种一棵树最好的时间，是现在。", a:"非洲谚语"},
  {t:"名人名言", q:"不积跬步，无以至千里。", a:"荀子"},
  {t:"名人名言", q:"宝剑锋从磨砺出，梅花香自苦寒来。", a:"《警世贤文》"},
  {t:"名人名言", q:"天行健，君子以自强不息。", a:"《周易》"},
  {t:"名人名言", q:"你今天的努力，是幸运的伏笔。", a:"佚名"},
  {t:"名人名言", q:"路漫漫其修远兮，吾将上下而求索。", a:"屈原"},
  {t:"名人名言", q:"穷且益坚，不坠青云之志。", a:"王勃"},
  {t:"名人名言", q:"长风破浪会有时，直挂云帆济沧海。", a:"李白"},
  {t:"名人名言", q:"会当凌绝顶，一览众山小。", a:"杜甫"},
  {t:"名人名言", q:"老骥伏枥，志在千里。", a:"曹操"}
];
function quoteHash(dateKey){
  var hash = 0;
  for(var i=0;i<dateKey.length;i++){
    hash = ((hash<<5)-hash)+dateKey.charCodeAt(i);
    hash = hash & hash;
  }
  return Math.abs(hash);
}
function renderQuote(dateKey, forceRandom){
  var idx = forceRandom ? Math.floor(Math.random()*QUOTES.length) : quoteHash(dateKey) % QUOTES.length;
  var item = QUOTES[idx];
  document.getElementById("quoteTitle").textContent = item.t;
  document.getElementById("quoteAuthor").textContent = "—— " + item.a;
  document.getElementById("quoteVerse").textContent = item.q;
}

function renderDay(){
  document.getElementById('monthView').style.display='none';
  document.getElementById('dayView').style.display='block';
  var k=state.day;
  document.getElementById('dayTitle').innerHTML=fmtCN(k)+'<span class="sub">'+k+'</span>';
  renderDayIllu();
  renderQuote(k);
  // 渲染心情
  var gd=getDay(k);
  document.querySelectorAll('.mood-btn').forEach(function(btn){
    btn.classList.toggle('active', gd.mood===btn.getAttribute('data-mood'));
  });
  // 渲染纪念日提醒
  var annivs=getAnnivsOfDate(k);
  var bannerEl=document.getElementById('annivBanner');
  if(annivs.length){
    bannerEl.innerHTML=annivs.map(function(a){
      return '<div class="anniv-banner"><span class="anniv-banner-icon">'+annivIcon(a.type)+'</span><div class="anniv-banner-text"><div class="anniv-banner-title">'+esc(a.name)+'</div><div class="anniv-banner-sub">今天是这个特别的日子</div></div></div>';
    }).join('');
  }else{
    bannerEl.innerHTML='';
  }

  document.getElementById('tabT').classList.toggle('active',state.tab==='t');
  document.getElementById('tabD').classList.toggle('active',state.tab==='d');
  document.getElementById('tabP').classList.toggle('active',state.tab==='p');
  document.getElementById('panelT').classList.toggle('active',state.tab==='t');
  document.getElementById('panelD').classList.toggle('active',state.tab==='d');
  document.getElementById('panelP').classList.toggle('active',state.tab==='p');

  renderTodoList(k,'t');
  renderTodoList(k,'p');
  var g=getDay(k);
  var ta=document.getElementById('diaryArea');
  if(document.activeElement!==ta) ta.value=g.d||'';
  updateDiaryStatus(false);
}

function renderTodoList(k,list){
  var g=getDay(k);
  var items=g[list]||[];
  var pending=items.filter(function(x){return !x.done;});
  var done=items.filter(function(x){return x.done;});
  function build(arr,emptyText){
    var html='';
    arr.forEach(function(it,i){
      var pri=it.priority||'normal';
      var priClass='priority-'+pri;
      var repeatHtml='';
      if(it.repeat&&it.repeat!=='none'){
        var repeatLabel=it.repeat==='daily'?'每天':it.repeat==='weekly'?'每周':'每月';
        repeatHtml='<span class="todo-repeat active" data-action="cycle-repeat" data-list="'+list+'" data-id="'+it.id+'" title="点击修改重复：'+repeatLabel+'">🔁 '+repeatLabel+'</span>';
      }else if(list==='t'){
        repeatHtml='<span class="todo-repeat" data-action="cycle-repeat" data-list="'+list+'" data-id="'+it.id+'" title="点击设置重复">🔁</span>';
      }
      html+='<li class="todo-item'+(it.done?' done':'')+'" data-id="'+it.id+'">'+
        '<span class="todo-priority '+priClass+'"></span>'+
        '<span class="todo-idx" data-action="cycle-priority" data-list="'+list+'" data-id="'+it.id+'" title="点击切换优先级：高/中/低">'+(i+1)+'.</span>'+
        '<label class="todo-cb" data-action="toggle-todo" data-list="'+list+'" data-id="'+it.id+'" aria-label="完成">'+(it.done?svgCheck():'')+'</label>'+
        '<span class="todo-text">'+esc(it.text)+'</span>'+repeatHtml+
        '<button class="todo-del" data-action="del-todo" data-list="'+list+'" data-id="'+it.id+'" aria-label="删除"><svg viewBox="0 0 24 24"><path d="M3 6h18M8 6V4h8v2M19 6l-1 14H6L5 6M10 11v6M14 11v6"/></svg></button>'+
        '</li>';
    });
    if(!arr.length) html='<li class="todo-item empty-state"><img class="empty-img" src="'+EMPTY_IMG+'" alt=""><span class="empty-text">'+emptyText+'</span></li>';
    return html;
  }
  if(list==='t'){
    document.getElementById('listT').innerHTML=build(pending, (done.length?'今天要做的事都完成啦':'还没有记录，从上面输入第一条吧。'));
    document.getElementById('listDoneT').innerHTML=build(done,'');
    document.getElementById('doneGroupT').style.display=done.length?'':'none';
    document.getElementById('countT').textContent=pending.length?('共 '+pending.length+' 条'):'';
    document.getElementById('countDoneT').textContent=done.length?('共 '+done.length+' 条'):'';
  }else{
    document.getElementById('listP').innerHTML=build(items,'还没有记录，从上面输入第一条吧。');
    document.getElementById('countP').textContent=items.length?('共 '+items.length+' 条 · 已完成 '+done.length+' 条'):'';
  }
}

function updateDiaryStatus(saved){
  var el=document.getElementById('diaryStatus');
  if(saved===true) el.textContent='已保存 · '+new Date().toTimeString().slice(0,5);
  else if(saved===false) el.textContent='日记自动保存在本机浏览器';
  else el.textContent='保存中…';
}

/* ===== 导出 / 导入 ===== */
function exportDay(k){
  var g=getDay(k);
  var lines=[];
  lines.push(fmtCN(k)+' 的记录');
  lines.push('');
  lines.push('【今日清单】');
  (g.t||[]).forEach(function(it,i){ lines.push((it.done?'[x] ':'[ ] ')+(i+1)+'. '+it.text); });
  if(!(g.t||[]).length) lines.push('（无）');
  lines.push('');
  lines.push('【日记】');
  lines.push(g.d&&g.d.trim()?g.d:'（无）');
  lines.push('');
  lines.push('【明日计划】');
  (g.p||[]).forEach(function(it,i){ lines.push((it.done?'[x] ':'[ ] ')+(i+1)+'. '+it.text); });
  if(!(g.p||[]).length) lines.push('（无）');
  download(k+'.txt', lines.join('\n'), 'text/plain;charset=utf-8');
}
function download(name,content,type){
  var blob=new Blob([content],{type:type});
  var a=document.createElement('a');
  a.href=URL.createObjectURL(blob); a.download=name;
  document.body.appendChild(a); a.click();
  setTimeout(function(){ URL.revokeObjectURL(a.href); a.remove(); },200);
}
function exportAll(){
  download('夜页手账备份-'+todayKey()+'.json', JSON.stringify(DB,null,2), 'application/json');
}
function importAll(file){
  var r=new FileReader();
  r.onload=function(){
    try{
      var obj=JSON.parse(r.result);
      if(!obj||typeof obj!=='object') throw 0;
      DB=obj; persist(); render();
      toast('导入成功，已合并覆盖当前数据');
    }catch(e){ toast('导入失败：文件格式不正确'); }
  };
  r.readAsText(file,'utf-8');
}

/* ===== 年月跳转 ===== */
function gotoMonth(m){
  state.view='month'; state.month=m; setHash(); render();
}
function changeMonth(delta){
  var p=state.month.split('-'); var d=new Date(+p[0],+p[1]-1+delta,1);
  gotoMonth(d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0'));
}

/* ===== 周视图导航 ===== */
function gotoWeek(dateKey){
  state.view='week'; state.week=getWeekStart(dateKey); setHash(); render();
}
function changeWeek(delta){
  var d=parseKey(state.week); d.setDate(d.getDate()+delta*7);
  gotoWeek(dayKey(d));
}

function initJump(){
  var ys=document.getElementById('yearSel'), ms=document.getElementById('monthSel');
  for(var y=1900;y<=2100;y++){
    var o=document.createElement('option'); o.value=String(y); o.textContent=y+'年'; ys.appendChild(o);
  }
  for(var m=1;m<=12;m++){
    var o2=document.createElement('option'); o2.value=String(m); o2.textContent=m+'月'; ms.appendChild(o2);
  }
  ys.addEventListener('change',function(){
    gotoMonth(String(this.value)+'-'+state.month.split('-')[1]);
  });
  ms.addEventListener('change',function(){
    gotoMonth(state.month.split('-')[0]+'-'+String(this.value).padStart(2,'0'));
  });
}

/* ===== 事件 ===== */
document.addEventListener('click',function(e){
  var el=e.target.closest('[data-action]');
  if(!el) return;
  var act=el.getAttribute('data-action');
  if(act==='prev-month'){
    changeMonth(-1);
  }else if(act==='next-month'){
    changeMonth(1);
  }else if(act==='goto-today'){
    var d=new Date(); gotoMonth(d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0'));
  }else if(act==='open-day'){
    state.view='day'; state.day=el.getAttribute('data-date'); state.tab='t'; setHash(); render();
  }else if(act==='open-month'){
    var d=parseKey(el.getAttribute('data-date'));
    gotoMonth(d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0'));
  }else if(act==='prev-day'||act==='next-day'){
    var dd=parseKey(state.day);
    dd.setDate(dd.getDate()+(act==='next-day'?1:-1));
    state.day=dayKey(dd); setHash(); render();
  }else if(act==='back'){
    var d=parseKey(state.day); state.view='month'; state.month=d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0'); setHash(); render();
  }else if(act==='set-tab'){
    state.tab=el.getAttribute('data-tab'); setHash(); render();
  }else if(act==='add-todo'){
    var list=el.getAttribute('data-list');
    var input=document.getElementById(list==='t'?'inputT':'inputP');
    addTodo(state.day,list,input.value);
  }else if(act==='toggle-todo'){
    toggleTodo(state.day,el.getAttribute('data-list'),el.getAttribute('data-id'));
  }else if(act==='del-todo'){
    delTodo(state.day,el.getAttribute('data-list'),el.getAttribute('data-id'));
  }else if(act==='export-day'){
    exportDay(state.day); toast('已导出为文本，可用 Word 打开');
  }else if(act==='export-all'){
    exportAll(); toast('已备份全部数据（JSON 文件）');
  }else if(act==='import-all'){
    document.getElementById('importFile').click();
  }else if(act==='refresh-daily'){
    loadQuote(true);
    try{ localStorage.removeItem(imgCacheKey(todayKey())); }catch(e){}
    var img=document.getElementById('dailyImg');
    document.getElementById('dailyCard').classList.remove('noimg');
    img.dataset.idx='0';
    img.src=animeURL(0);
    toast('已换新语录和新插图');
  }else if(act==='refresh-quote'){
    renderQuote(state.day, true);
    toast('已换新语录');
  }else if(act==='refresh-day-illu'){
    try{ localStorage.removeItem(imgCacheKey(state.day)); }catch(e){}
    var img2=document.getElementById('dayIlluImg');
    document.getElementById('dayIllu').classList.remove('noimg');
    img2.dataset.idx='0';
    img2.src=animeURL(0);
    toast('已换新插图');
  }else if(act==='cycle-priority'){
    e.preventDefault(); e.stopPropagation();
    var gp=getDay(state.day); var itp=gp[el.getAttribute('data-list')].find(function(x){return x.id===el.getAttribute('data-id');});
    if(itp){
      var cur=itp.priority||'normal';
      itp.priority=cur==='normal'?'high':cur==='high'?'low':'normal';
      persist(); renderTodoList(state.day,el.getAttribute('data-list'));
      toast('优先级：'+(itp.priority==='high'?'高':itp.priority==='low'?'低':'普通'));
    }
  }else if(act==='cycle-repeat'){
    e.preventDefault(); e.stopPropagation();
    var gr=getDay(state.day); var itr=gr[el.getAttribute('data-list')].find(function(x){return x.id===el.getAttribute('data-id');});
    if(itr){
      var curR=itr.repeat||'none';
      itr.repeat=curR==='none'?'daily':curR==='daily'?'weekly':curR==='weekly'?'monthly':'none';
      itr.repeatFrom=itr.repeat!=='none'?state.day:null;
      persist(); renderTodoList(state.day,el.getAttribute('data-list'));
      toast(itr.repeat==='none'?'已取消重复':'重复：'+(itr.repeat==='daily'?'每天':itr.repeat==='weekly'?'每周':'每月'));
      if(itr.repeat!=='none') processRepeatTasks();
    }
  }else if(act==='manage-anniv'){
    renderAnnivList();
    document.getElementById('annivModal').classList.add('show');
  }else if(act==='close-anniv-modal'){
    document.getElementById('annivModal').classList.remove('show');
  }else if(act==='add-anniv'){
    var name=document.getElementById('annivName').value.trim();
    var date=document.getElementById('annivDate').value;
    var type=document.getElementById('annivType').value;
    if(!name){ toast('请输入纪念日名称'); return; }
    if(!date){ toast('请选择日期'); return; }
    addAnniv(name,date,type);
    document.getElementById('annivName').value='';
    document.getElementById('annivDate').value='';
    renderAnnivList();
    render();
    toast('已添加纪念日');
  }else if(act==='cycle-theme'){
    cycleTheme();
  }else if(act==='week-summary'){
    weekSummary();
  }else if(act==='month-summary'){
    monthSummary();
  }else if(act==='close-summary-modal'){
    document.getElementById('summaryModal').classList.remove('show');
  }else if(act==='inspire'){
    showInspiration();
  }else if(act==='export-img'){
    exportHandbookImage();
  }else if(act==='view-week'){
    var d=new Date(); gotoWeek(dayKey(d));
  }else if(act==='view-month'){
    var d2=parseKey(state.week); gotoMonth(d2.getFullYear()+'-'+String(d2.getMonth()+1).padStart(2,'0'));
  }else if(act==='prev-week'){
    changeWeek(-1);
  }else if(act==='next-week'){
    changeWeek(1);
  }else if(act==='goto-today-week'){
    gotoWeek(todayKey());
  }else if(act==='open-day-week'){
    state.view='day'; state.day=el.getAttribute('data-date'); state.tab='t'; setHash(); render();
  }else if(act==='data-stats'){
    showDataStats();
  }else if(act==='clear-all'){
    clearAllData();
  }
});

// 心情按钮事件
document.addEventListener('click',function(e){
  var btn=e.target.closest('.mood-btn');
  if(!btn) return;
  var mood=btn.getAttribute('data-mood');
  var g=getDay(state.day);
  if(g.mood===mood){ g.mood=null; }
  else{ g.mood=mood; }
  persist(); render(); markActive(state.day);
});

// 点击弹窗外部关闭
var _annivModal=document.getElementById('annivModal');
if(_annivModal) _annivModal.addEventListener('click',function(e){
  if(e.target===this) this.classList.remove('show');
});
var _summaryModal=document.getElementById('summaryModal');
if(_summaryModal) _summaryModal.addEventListener('click',function(e){
  if(e.target===this) this.classList.remove('show');
});

function renderAnnivList(){
  var list=getAnnivs();
  var el=document.getElementById('annivList');
  if(!list.length){ el.innerHTML='<div style="text-align:center;color:var(--ink-faint);padding:20px;font-size:14px;">还没有添加纪念日</div>'; return; }
  el.innerHTML=list.map(function(a){
    return '<div class="anniv-list-item"><span class="anniv-list-icon">'+annivIcon(a.type)+'</span><div class="anniv-list-info"><div class="anniv-list-name">'+esc(a.name)+'</div><div class="anniv-list-date">'+a.date+'</div></div><button class="anniv-list-del" data-action="del-anniv" data-id="'+a.id+'"><svg viewBox="0 0 24 24" style="width:16px;height:16px;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;"><path d="M3 6h18M8 6V4h8v2M19 6l-1 14H6L5 6"/></svg></button></div>';
  }).join('');
}

// 纪念日删除事件（委托）
document.addEventListener('click',function(e){
  var del=e.target.closest('[data-action="del-anniv"]');
  if(!del) return;
  delAnniv(del.getAttribute('data-id'));
  renderAnnivList();
  render();
  toast('已删除纪念日');
});

function keydownHandler(e){
  if(e.key==='Enter'&&e.target.id==='inputT'){ e.preventDefault(); addTodo(state.day,'t',e.target.value); }
  else if(e.key==='Enter'&&e.target.id==='inputP'){ e.preventDefault(); addTodo(state.day,'p',e.target.value); }
}
document.addEventListener('keydown',function(e){
  var tag=(e.target&&e.target.tagName)||'';
  if(tag==='INPUT'||tag==='TEXTAREA'||tag==='SELECT') return;
  if(state.view!=='month') return;
  if(e.key==='ArrowLeft'){ e.preventDefault(); changeMonth(-1); }
  else if(e.key==='ArrowRight'){ e.preventDefault(); changeMonth(1); }
});
document.addEventListener('keydown',keydownHandler);
document.getElementById('importFile').addEventListener('change',function(e){
  if(e.target.files&&e.target.files[0]) importAll(e.target.files[0]);
  e.target.value='';
});

var diaryTimer=null;
document.getElementById('diaryArea').addEventListener('input',function(){
  var ta=this, k=state.day;
  updateDiaryStatus(null);
  clearTimeout(diaryTimer);
  diaryTimer=setTimeout(function(){
    if(state.view!=='day') return;
    getDay(state.day).d=ta.value; persist(); updateDiaryStatus(true); markActive(state.day);
  },800);
});

function addTodo(k,list,text){
  text=(text||'').trim();
  if(!text){ toast('先写点内容再添加'); return; }
  var g=getDay(k);
  g[list].push({id:Date.now()+''+Math.floor(Math.random()*999), text:text, done:false, priority:'normal', repeat:'none', repeatFrom:null});
  persist(); renderTodoList(k,list);
  markActive(k);
  var input=document.getElementById(list==='t'?'inputT':'inputP');
  input.value=''; input.focus();
}
function toggleTodo(k,list,id){
  var g=getDay(k); var it=g[list].find(function(x){return x.id===id;});
  if(it){ it.done=!it.done; persist(); renderTodoList(k,list); markActive(k); }
}
function delTodo(k,list,id){
  var g=getDay(k);
  g[list]=g[list].filter(function(x){return x.id!==id;});
  persist(); renderTodoList(k,list); markActive(k);
}

/* ===== 每日插图 + 励志语录 ===== */
var QUOTE_KEY='nightpages_quote';
var FALLBACK_QUOTES=[
  '不积跬步，无以至千里。','千里之行，始于足下。','宝剑锋从磨砺出，梅花香自苦寒来。',
  '星光不问赶路人，时光不负有心人。','种一棵树最好的时间是十年前，其次是现在。',
  '生活明朗，万物可爱，人间值得，未来可期。','世上无难事，只怕有心人。'
];
var IMG_KEY='nightpages_img';
var ANIME_APIS=['https://t.alcy.cc/moez','https://www.dmoe.cc/random.php'];
function picsumURL(){
  var tk=todayKey();
  var w=window.innerWidth<640?800:1600;
  return 'https://picsum.photos/seed/nightpages-'+tk+'/'+w+'/'+Math.round(w*0.56)+'?auto=format';
}
function animeURL(idx){
  var base=ANIME_APIS[idx]||ANIME_APIS[0];
  return base+(base.indexOf('?')>=0?'&':'?')+'_t='+Date.now()+'_'+Math.floor(Math.random()*100000);
}
function imgCacheKey(dateKey){ return IMG_KEY+'_'+dateKey; }
function getCachedImg(dateKey){
  try{ return localStorage.getItem(imgCacheKey(dateKey))||''; }catch(e){ return ''; }
}
function setCachedImg(dateKey,url){
  try{ localStorage.setItem(imgCacheKey(dateKey),url); }catch(e){}
}
function maybeCacheImg(img,dateKey){
  try{
    var cur=img.currentSrc||img.src||'';
    if(cur&&cur.indexOf(ANIME_APIS[0])<0&&cur.indexOf(ANIME_APIS[1])<0&&cur.indexOf('picsum')<0){
      setCachedImg(dateKey,cur);
    }
  }catch(e){}
}
function dailyImgURL(dateKey){
  dateKey=dateKey||todayKey();
  var u=getCachedImg(dateKey);
  if(u) return u;
  return animeURL(0);
}
function setQuote(q,f){
  document.getElementById('dailyQuote').textContent=q;
  document.getElementById('dailyFrom').textContent=f?('—— '+f):'';
}
function loadQuote(force){
  var el=document.getElementById('dailyQuote');
  var tk=todayKey();
  var cached=null;
  try{ cached=JSON.parse(localStorage.getItem(QUOTE_KEY))||null; }catch(e){}
  if(!force&&cached&&cached.d===tk){ setQuote(cached.q,cached.f||''); return; }
  el.textContent='正在摘取今日语录…';
  document.getElementById('dailyFrom').textContent='';
  fetch('https://v1.hitokoto.cn/?c=d&c=i&c=k&encode=json')
    .then(function(r){ return r.json(); })
    .then(function(j){
      var q=(j&&j.hitokoto)||''; var f=(j&&j.from)||'';
      if(!q) throw new Error('empty');
      try{ localStorage.setItem(QUOTE_KEY, JSON.stringify({d:tk,q:q,f:f})); }catch(e){}
      setQuote(q,f);
    })
    .catch(function(){
      var i=Math.floor(Math.random()*FALLBACK_QUOTES.length);
      setQuote(FALLBACK_QUOTES[i],'本机备用语录');
    });
}
function renderDaily(){
  var card=document.getElementById('dailyCard');
  var img=document.getElementById('dailyImg');
  img.onerror=function(){
    var idx=parseInt(img.dataset.idx||'0',10)+1;
    if(idx<ANIME_APIS.length){ img.dataset.idx=idx; img.src=animeURL(idx); }
    else if(idx===ANIME_APIS.length){ img.dataset.idx=idx; img.src=picsumURL(); }
    else{ card.classList.add('noimg'); }
  };
  img.onload=function(){
    card.classList.remove('noimg');
    maybeCacheImg(img,todayKey());
  };
  img.dataset.idx='0';
  img.src=dailyImgURL(todayKey());
  loadQuote(false);
}

function renderDayIllu(){
  var card=document.getElementById('dayIllu');
  var img=document.getElementById('dayIlluImg');
  img.onerror=function(){
    var idx=parseInt(img.dataset.idx||'0',10)+1;
    if(idx<ANIME_APIS.length){ img.dataset.idx=idx; img.src=animeURL(idx); }
    else if(idx===ANIME_APIS.length){ img.dataset.idx=idx; img.src=picsumURL(); }
    else{ card.classList.add('noimg'); }
  };
  img.onload=function(){
    card.classList.remove('noimg');
    maybeCacheImg(img,state.day);
  };
  img.dataset.idx='0';
  img.src=dailyImgURL(state.day);
  var parts=state.day.split('-');
  document.getElementById('dayIlluTag').textContent=(parseInt(parts[1],10)+'月'+parseInt(parts[2],10)+'日')+' · 每日一图';
}

/* ===== 启动 ===== */
DB=load();
initJump();
if(!state.month) initMonth();
parseHash();
if(state.view==='week'&&!state.week) state.week=getWeekStart(todayKey());
processRepeatTasks();
setTheme(getTheme());
render();
function render(){
  if(state.view==='day'&&!state.day){ state.view='month'; }
  if(state.view==='day') renderDay();
  else if(state.view==='week') renderWeek();
  else renderMonth();
}

/* ===== 渲染：周 ===== */
function getWeekStart(dateKey){
  var d=parseKey(dateKey);
  var day=d.getDay()||7; // 周一为1
  d.setDate(d.getDate()-day+1);
  return dayKey(d);
}
function renderWeek(){
  document.getElementById('monthView').style.display='none';
  document.getElementById('weekView').style.display='block';
  document.getElementById('dayView').style.display='none';
  if(!state.week) state.week=getWeekStart(todayKey());
  var weekStart=parseKey(state.week);
  var weekEnd=new Date(weekStart); weekEnd.setDate(weekStart.getDate()+6);
  document.getElementById('weekTitle').textContent=
    (weekStart.getMonth()+1)+'月'+weekStart.getDate()+'日 - '+(weekEnd.getMonth()+1)+'月'+weekEnd.getDate()+'日';

  // 周统计
  var total=0,done=0,diaryDays=0,moodCount={};
  var days=[];
  for(var i=0;i<7;i++){
    var d=new Date(weekStart); d.setDate(weekStart.getDate()+i);
    var k=dayKey(d);
    days.push(k);
    var g=DB[k];
    if(g){
      if(g.t){ total+=g.t.length; done+=g.t.filter(function(x){return x.done;}).length; }
      if(g.d&&g.d.trim()) diaryDays++;
      if(g.mood){ moodCount[g.mood]=(moodCount[g.mood]||0)+1; }
    }
  }
  var rate=total?Math.round(done/total*100):0;
  var moodTop=Object.entries(moodCount).sort(function(a,b){return b[1]-a[1];})[0];
  var summaryHtml='<div class="stat-card" style="flex:1;min-width:120px;"><div class="stat-label">本周完成率</div><div class="stat-value">'+rate+'%</div></div>';
  summaryHtml+='<div class="stat-card" style="flex:1;min-width:120px;"><div class="stat-label">本周任务</div><div class="stat-value">'+done+'/'+total+'</div></div>';
  summaryHtml+='<div class="stat-card" style="flex:1;min-width:120px;"><div class="stat-label">写日记</div><div class="stat-value">'+diaryDays+' 天</div></div>';
  if(moodTop){ summaryHtml+='<div class="stat-card" style="flex:1;min-width:120px;"><div class="stat-label">本周心情</div><div class="stat-value" style="font-size:24px;">'+MOODS[moodTop[0]].icon+' '+MOODS[moodTop[0]].name+'</div></div>'; }
  document.getElementById('weekSummaryBar').innerHTML=summaryHtml;

  // 7天卡片
  var wdNames=['一','二','三','四','五','六','日'];
  var tk=todayKey();
  var html='';
  days.forEach(function(k,idx){
    var d=parseKey(k);
    var g=DB[k];
    var isToday=k===tk;
    var moodIcon='';
    if(g&&g.mood&&MOODS[g.mood]) moodIcon=MOODS[g.mood].icon;
    var tasksHtml='';
    var taskList=(g&&g.t)?g.t.slice(0,4):[];
    taskList.forEach(function(t){
      tasksHtml+='<div class="week-day-task'+(t.done?' done':'')+(t.priority==='high'?' high':'')+'">'+esc(t.text)+'</div>';
    });
    if(g&&g.t&&g.t.length>4){ tasksHtml+='<div class="week-day-more">+'+(g.t.length-4)+' 更多</div>'; }
    var dayDone=(g&&g.t)?g.t.filter(function(x){return x.done;}).length:0;
    var dayTotal=(g&&g.t)?g.t.length:0;
    var hasDiary=g&&g.d&&g.d.trim();
    html+='<div class="week-day'+(isToday?' today':'')+'" data-action="open-day-week" data-date="'+k+'">';
    html+='<div class="week-day-num">'+d.getDate()+'</div>';
    html+='<div class="week-day-wd">周'+wdNames[idx]+'</div>';
    html+='<div class="week-day-mood">'+moodIcon+'</div>';
    html+='<div class="week-day-tasks">'+tasksHtml+'</div>';
    html+='<div class="week-day-footer">';
    html+='<span class="week-day-rate">'+(dayTotal?dayDone+'/'+dayTotal:'')+'</span>';
    html+='<span class="week-day-diary">'+(hasDiary?'📝':'')+'</span>';
    html+='</div></div>';
  });
  document.getElementById('weekGrid').innerHTML=html;
}

})();
</script>
<script>
// 注册 Service Worker（PWA 离线支持）
if ('serviceWorker' in navigator) {
  window.addEventListener('load', function() {
    navigator.serviceWorker.register('./service-worker.js').then(function(reg) {
      console.log('Service Worker 注册成功', reg.scope);
    }).catch(function(err) {
      console.log('Service Worker 注册失败', err);
    });
  });
}
</script>

<!-- ===== 纪念日管理弹窗 ===== -->
<div class="modal-overlay" id="annivModal">
  <div class="modal">
    <div class="modal-title">
      管理纪念日
      <button class="modal-close" data-action="close-anniv-modal">✕</button>
    </div>
    <div id="annivList"></div>
    <div style="height:16px"></div>
    <input class="modal-input" id="annivName" placeholder="纪念日名称，如：妈妈生日、结婚纪念日">
    <div class="modal-row">
      <input class="modal-input" id="annivDate" type="date" style="flex:1;margin-bottom:0">
      <select class="modal-select" id="annivType">
        <option value="birthday">🎂 生日</option>
        <option value="anniversary">💝 纪念日</option>
        <option value="other">📌 其他</option>
      </select>{
  "name": "夜页·每日手账",
  "short_name": "夜页手账",
  "description": "一款温暖治愈的每日手账应用，记录任务、日记、心情与灵感",
  "start_url": "./index.html",
  "scope": "./",
  "display": "standalone",
  "orientation": "portrait",
  "background_color": "#1d212a",
  "theme_color": "#1d212a",[service-worker.js](https://github.com/user-attachments/files/32342922/service-worker.js)


  "lang": "zh-CN",
  "icons": [
    {
      "src": "icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "any maskable"
    },
    {
      "src": "icons/icon-512.png",
      "sizes": "512x512",/* 夜页·每日手账 Service Worker - 离线缓存 */
const CACHE_NAME = 'nightpages-v1';
const CORE_FILES = [
  './index.html',
  './manifest.json',
  './icons/icon-192.png',
  './icons/icon-512.png'
];

// 安装：缓存核心文件
self.addEventListener('install', function(event) {
  event.waitUntil(
    caches.open(CACHE_NAME).then(function(cache) {
      return cache.addAll(CORE_FILES);
    }).then(function() {
      return self.skipWaiting();
    })
  );
});

// 激活：清理旧缓存
self.addEventListener('activate', function(event) {
  event.waitUntil(
    caches.keys().then(function(cacheNames) {
      return Promise.all(
        cacheNames.filter(function(name) {
          return name !== CACHE_NAME;
        }).map(function(name) {
          return caches.delete(name);
        })
      );
    }).then(function() {
      return self.clients.claim();
    })
  );
});

// 请求拦截：核心文件优先缓存，外部资源网络优先
self.addEventListener('fetch', function(event) {
  var url = new URL(event.request.url);

  // 只处理 GET 请求
  if (event.request.method !== 'GET') return;

  // 同源核心文件：缓存优先
  if (url.origin === location.origin) {
    event.respondWith(
      caches.match(event.request).then(function(cached) {
        if (cached) return cached;
        return fetch(event.request).then(function(response) {
          // 缓存成功的响应
          if (response && response.status === 200) {
            var clone = response.clone();
            caches.open(CACHE_NAME).then(function(cache) {
              cache.put(event.request, clone);
            });
          }
          return response;
        }).catch(function() {
          // 网络失败，返回缓存的 index.html（单页应用回退）
          return caches.match('./index.html');
        });
      })
    );
    return;
  }

  // 外部资源（CDN、字体、图片）：网络优先，失败用缓存
  event.respondWith(
    fetch(event.request).then(function(response) {
      if (response && response.status === 200) {
        var clone = response.clone();
        caches.open(CACHE_NAME).then(function(cache) {
          cache.put(event.request, clone);
        });
      }
      return response;
    }).catch(function() {
      return caches.match(event.request);
    })
  );
});
      "type": "image/png",
      "purpose": "any maskable"
    }
  ]
}
    </div>
    <div style="display:flex;gap:10px">
      <button class="modal-btn primary" data-action="add-anniv">添加纪念日</button>
      <button class="modal-btn ghost" data-action="close-anniv-modal">取消</button>
    </div>
  </div>
</div>

<!-- ===== 总结弹窗 ===== -->
<div class="modal-overlay" id="summaryModal">
  <div class="modal">
    <div class="modal-title">
      <span id="summaryTitle">总结</span>
      <button class="modal-close" data-action="close-summary-modal">✕</button>
    </div>
    <div id="summaryContent"></div>
    <div style="height:16px"></div>
    <div style="display:flex;gap:10px">
      <button class="modal-btn primary" data-action="close-summary-modal">知道了</button>
    </div>
  </div>
</div>
</body>
</html>[manifest.json](https://github.com/user-attachments/files/32342906/manifest.json)

