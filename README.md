<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CollegeHub - Academic Portal</title>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --blue:#1a3a6e;--blue2:#2563eb;--blue3:#1e40af;
  --gray:#f5f5f5;--gray2:#e5e7eb;--gray3:#9ca3af;--gray4:#6b7280;--gray5:#374151;
  --white:#ffffff;--text:#111827;--sidebar-w:160px;
  --font:'Plus Jakarta Sans',sans-serif;
}
body{font-family:var(--font);background:#f3f4f6;color:var(--text);font-size:14px}
a{text-decoration:none;color:inherit}
button{font-family:var(--font);cursor:pointer}
input,textarea,select{font-family:var(--font)}

/* === PAGE SYSTEM === */
.page{display:none;min-height:100vh}
.page.active{display:flex}

/* === AUTH PAGES === */
#page-login,#page-register{
  background:#e8edf5;
  align-items:center;justify-content:center;min-height:100vh;
}
.auth-card{background:var(--white);border-radius:16px;padding:48px 40px;width:380px;text-align:center;box-shadow:0 4px 24px rgba(0,0,0,.08)}
.auth-icon{width:72px;height:72px;background:var(--blue);border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 12px;color:white;font-size:28px}
.auth-title{font-size:22px;font-weight:700;color:var(--blue);margin-bottom:24px;letter-spacing:1px}
.auth-label{text-align:left;font-size:12px;font-weight:600;color:var(--gray5);margin-bottom:4px;display:block}
.auth-label span{color:#e53e3e}
.auth-input{width:100%;border:1px solid var(--gray2);border-radius:6px;padding:9px 12px;font-size:13px;outline:none;margin-bottom:14px;color:var(--text)}
.auth-input:focus{border-color:var(--blue2)}
.auth-btn{width:100%;background:var(--blue);color:white;border:none;border-radius:6px;padding:11px;font-size:14px;font-weight:600;margin-top:4px}
.auth-btn:hover{background:var(--blue3)}
.auth-link{font-size:12px;color:var(--gray4);margin-top:14px;display:block}
.auth-link a{color:var(--blue2);font-weight:600}
.forgot{font-size:11px;color:var(--blue2);float:right;margin-top:-10px;margin-bottom:10px}
.pw-wrap{position:relative;margin-bottom:14px}
.pw-wrap input{margin-bottom:0;padding-right:36px}
.pw-wrap .eye{position:absolute;right:10px;top:50%;transform:translateY(-50%);color:var(--gray3);font-size:14px;cursor:pointer}
.pw-lock{position:absolute;left:10px;top:50%;transform:translateY(-50%);color:var(--gray3);font-size:14px}
.pw-wrap input{padding-left:32px}

/* Register */
.reg-card{background:var(--white);border-radius:16px;padding:40px 36px;width:480px;box-shadow:0 4px 24px rgba(0,0,0,.08)}
.reg-title{font-size:26px;font-weight:700;color:var(--text);margin-bottom:4px}
.reg-sub{font-size:13px;color:var(--gray4);margin-bottom:24px;text-align:center}
.reg-row{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.check-row{display:flex;align-items:center;gap:8px;margin:12px 0;font-size:12px;color:var(--gray4)}
.check-row a{color:var(--blue2)}
.reg-bg{position:absolute;bottom:0;right:0;opacity:.07;font-size:160px;color:var(--blue);pointer-events:none}
.reg-card{position:relative;overflow:hidden}

/* === MAIN LAYOUT === */
.app-layout{display:flex;flex-direction:column;width:100%;min-height:100vh}
.topbar{background:white;border-bottom:1px solid var(--gray2);padding:0 24px;height:52px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100}
.topbar-logo{display:flex;align-items:center;gap:8px;font-size:15px;font-weight:700;color:var(--blue)}
.topbar-logo i{font-size:20px;color:var(--blue2)}
.topbar-actions{display:flex;align-items:center;gap:16px}
.topbar-actions i{font-size:17px;color:var(--gray4);cursor:pointer}
.topbar-actions i:hover{color:var(--blue2)}
.avatar{width:30px;height:30px;border-radius:50%;background:linear-gradient(135deg,#e2a03f,#f59e0b);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;color:white;cursor:pointer}
.btn-signup{border:1.5px solid var(--blue);color:var(--blue);background:none;border-radius:6px;padding:5px 14px;font-size:13px;font-weight:600}
.btn-signin{background:var(--blue);color:white;border:none;border-radius:6px;padding:5px 14px;font-size:13px;font-weight:600;margin-left:8px}
.btn-signup:hover{background:var(--blue);color:white}
.btn-signin:hover{background:var(--blue3)}

.main-body{display:flex;flex:1}
.sidebar{width:var(--sidebar-w);background:white;border-right:1px solid var(--gray2);padding:16px 0;display:flex;flex-direction:column;justify-content:space-between;position:sticky;top:52px;height:calc(100vh - 52px);overflow-y:auto}
.sidebar-section{padding:0 12px}
.sidebar-brand{display:flex;align-items:center;gap:8px;padding:10px 12px 16px;border-bottom:1px solid var(--gray2);margin-bottom:8px}
.sidebar-brand-icon{width:32px;height:32px;background:linear-gradient(135deg,var(--blue),var(--blue2));border-radius:8px;display:flex;align-items:center;justify-content:center;color:white;font-size:14px}
.sidebar-brand-text{font-size:11px;font-weight:700;color:var(--blue);line-height:1.2}
.sidebar-brand-sub{font-size:9px;color:var(--gray3);font-weight:500;letter-spacing:.5px}
.nav-item{display:flex;align-items:center;gap:10px;padding:9px 12px;border-radius:8px;font-size:13px;font-weight:500;color:var(--gray4);cursor:pointer;margin-bottom:2px;transition:all .15s}
.nav-item:hover{background:var(--gray);color:var(--blue2)}
.nav-item.active{background:#eff6ff;color:var(--blue2);font-weight:600}
.nav-item i{width:16px;font-size:15px}
.sidebar-bottom{padding:12px}
.sidebar-bottom .nav-item{font-size:12px}

.content{flex:1;padding:24px;overflow-y:auto}

/* === DASHBOARD === */
.welcome-banner{background:linear-gradient(135deg,var(--blue) 0%,var(--blue2) 100%);border-radius:14px;padding:32px;color:white;margin-bottom:24px;position:relative;overflow:hidden}
.welcome-banner::after{content:'';position:absolute;right:-40px;top:-40px;width:200px;height:200px;background:rgba(255,255,255,.05);border-radius:50%}
.welcome-banner h1{font-size:22px;font-weight:700;margin-bottom:8px}
.welcome-banner p{font-size:13px;opacity:.85;margin-bottom:20px;max-width:380px;line-height:1.6}
.btn-explore{background:white;color:var(--blue);border:none;border-radius:8px;padding:10px 20px;font-size:13px;font-weight:700}
.btn-explore:hover{background:var(--gray)}

.section-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px}
.section-title{font-size:15px;font-weight:700;color:var(--text)}
.view-all{font-size:12px;color:var(--blue2);font-weight:600;cursor:pointer}
.view-all:hover{text-decoration:underline}

.courses-row{display:flex;gap:14px;overflow-x:auto;padding-bottom:4px}
.course-card{min-width:140px;background:white;border-radius:10px;border:1px solid var(--gray2);overflow:hidden;flex-shrink:0}
.course-card:hover{box-shadow:0 4px 12px rgba(0,0,0,.08)}
.course-thumb{height:80px;object-fit:cover;width:100%;background:#1e3a6e;display:flex;align-items:center;justify-content:center;position:relative}
.course-tag{position:absolute;top:6px;left:6px;background:rgba(255,255,255,.2);color:white;font-size:8px;font-weight:700;padding:2px 6px;border-radius:4px;letter-spacing:.5px}
.course-thumb i{font-size:24px;color:rgba(255,255,255,.7)}
.course-info{padding:8px}
.course-rating{display:flex;align-items:center;gap:3px;margin-bottom:4px;font-size:11px;color:var(--gray4)}
.course-rating i{color:#f59e0b;font-size:10px}
.course-name{font-size:11px;font-weight:600;color:var(--text);line-height:1.3;margin-bottom:8px}
.btn-detail{width:100%;border:1px solid var(--gray2);background:none;border-radius:6px;padding:5px;font-size:11px;color:var(--gray5);font-weight:500}
.btn-detail:hover{background:var(--blue2);color:white;border-color:var(--blue2)}

.discussion-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.disc-card{background:white;border-radius:10px;border:1px solid var(--gray2);padding:14px}
.disc-card:hover{box-shadow:0 2px 8px rgba(0,0,0,.06)}
.disc-user{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.disc-avatar{width:28px;height:28px;border-radius:50%;background:var(--blue2);display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:700;color:white;flex-shrink:0}
.disc-username{font-size:12px;font-weight:600;color:var(--text)}
.disc-time{font-size:10px;color:var(--gray3)}
.disc-likes{margin-left:auto;font-size:11px;color:var(--gray3);display:flex;align-items:center;gap:4px}
.disc-title{font-size:12px;font-weight:700;color:var(--text);margin-bottom:6px;line-height:1.4}
.disc-body{font-size:11px;color:var(--gray4);line-height:1.5;margin-bottom:10px}
.disc-actions{display:flex;gap:14px}
.disc-action{display:flex;align-items:center;gap:4px;font-size:11px;color:var(--blue2);font-weight:500;cursor:pointer}
.disc-action i{font-size:12px}

/* === MY COURSES === */
.courses-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:14px;margin-bottom:28px}
.course-card-v{background:white;border-radius:10px;border:1px solid var(--gray2);overflow:hidden}
.course-card-v .course-thumb{height:90px}

.downloads-table{background:white;border-radius:10px;border:1px solid var(--gray2);overflow:hidden}
.table-header{display:grid;grid-template-columns:2fr 1fr 100px 100px;gap:0;padding:10px 16px;border-bottom:1px solid var(--gray2)}
.table-header span{font-size:11px;font-weight:700;color:var(--gray4);text-transform:uppercase;letter-spacing:.5px}
.table-row{display:grid;grid-template-columns:2fr 1fr 100px 100px;gap:0;padding:12px 16px;border-bottom:1px solid var(--gray2);align-items:center}
.table-row:last-child{border-bottom:none}
.table-row:hover{background:#fafafa}
.file-info{display:flex;align-items:center;gap:10px}
.file-icon{width:28px;height:28px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0}
.file-icon.pdf{background:#fee2e2;color:#dc2626}
.file-icon.ppt{background:#fef3c7;color:#d97706}
.file-icon.doc{background:#dbeafe;color:#1d4ed8}
.file-name{font-size:12px;font-weight:600;color:var(--text)}
.file-date{font-size:10px;color:var(--gray3);margin-top:1px}
.file-subject{font-size:12px;color:var(--gray4)}
.file-size{font-size:12px;color:var(--gray4)}
.file-actions{display:flex;align-items:center;gap:8px}
.btn-open{background:none;border:1px solid var(--gray2);border-radius:6px;padding:5px 14px;font-size:11px;color:var(--gray5);font-weight:500}
.btn-open:hover{background:var(--blue2);color:white;border-color:var(--blue2)}

/* === RESEARCH === */
.research-layout{display:flex;gap:20px}
.filter-panel{width:200px;background:white;border-radius:10px;border:1px solid var(--gray2);padding:16px;flex-shrink:0;height:fit-content}
.filter-title{font-size:12px;font-weight:700;color:var(--gray5);margin-bottom:12px;text-transform:uppercase;letter-spacing:.5px}
.filter-label{font-size:11px;font-weight:700;color:var(--gray4);margin-bottom:6px;display:block}
.filter-select{width:100%;border:1px solid var(--gray2);border-radius:6px;padding:7px 10px;font-size:12px;color:var(--text);outline:none;margin-bottom:14px;appearance:none;background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%236b7280' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E") no-repeat right 10px center,white}
.btn-search-filter{width:100%;background:var(--blue);color:white;border:none;border-radius:8px;padding:10px;font-size:13px;font-weight:600}
.search-bar{display:flex;gap:0;margin-bottom:20px}
.search-input{flex:1;border:1px solid var(--gray2);border-radius:8px 0 0 8px;padding:10px 14px;font-size:13px;outline:none}
.search-input:focus{border-color:var(--blue2)}
.btn-search{background:var(--blue);color:white;border:none;border-radius:0 8px 8px 0;padding:0 20px;font-size:13px;font-weight:600}
.research-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px;flex:1}
.research-card{background:white;border-radius:10px;border:1px solid var(--gray2);overflow:hidden}
.research-thumb{height:110px;background:#1e3a6e;display:flex;align-items:center;justify-content:center;position:relative}
.research-thumb img{width:100%;height:100%;object-fit:cover}
.research-tag{position:absolute;top:8px;left:8px;background:rgba(255,255,255,.25);color:white;font-size:9px;font-weight:700;padding:3px 8px;border-radius:4px;letter-spacing:.5px}
.research-info{padding:12px}
.research-rating{display:flex;align-items:center;gap:3px;font-size:11px;color:var(--gray4);margin-bottom:4px}
.research-rating i{color:#f59e0b;font-size:10px}
.research-name{font-size:13px;font-weight:700;color:var(--text);margin-bottom:10px}
.btn-detail-lg{border:1px solid var(--gray2);background:none;border-radius:6px;padding:7px 18px;font-size:12px;color:var(--gray5);font-weight:500}
.btn-detail-lg:hover{background:var(--blue2);color:white;border-color:var(--blue2)}
.pagination{display:flex;align-items:center;justify-content:center;gap:6px;margin-top:20px}
.page-btn{width:30px;height:30px;border-radius:6px;border:1px solid var(--gray2);background:none;font-size:12px;cursor:pointer;display:flex;align-items:center;justify-content:center;color:var(--gray4)}
.page-btn.active{background:var(--blue2);color:white;border-color:var(--blue2)}
.page-btn:hover:not(.active){background:var(--gray)}

/* === DISCUSSION === */
.discussion-hero{background:white;border-radius:12px;border:1px solid var(--gray2);padding:32px;text-align:center;margin-bottom:20px}
.discussion-hero h2{font-size:26px;font-weight:700;color:var(--text);margin-bottom:16px;font-style:italic}
.btn-ask{background:var(--blue);color:white;border:none;border-radius:8px;padding:10px 28px;font-size:14px;font-weight:600}
.filter-tags{display:flex;align-items:center;gap:8px;margin-bottom:16px;flex-wrap:wrap}
.filter-tags span{font-size:11px;font-weight:600;color:var(--gray4)}
.tag{background:#dbeafe;color:var(--blue2);border:none;border-radius:20px;padding:4px 14px;font-size:12px;font-weight:600;cursor:pointer}
.tag.active{background:var(--blue2);color:white}
.sort-row{display:flex;align-items:center;justify-content:flex-end;margin-bottom:14px;gap:8px}
.sort-row span{font-size:12px;color:var(--gray4)}
.sort-select{border:1px solid var(--gray2);border-radius:6px;padding:5px 10px;font-size:12px;outline:none}
.disc-list{display:flex;flex-direction:column;gap:12px}
.disc-list-card{background:white;border-radius:10px;border:1px solid var(--gray2);padding:16px}
.disc-list-card:hover{box-shadow:0 2px 8px rgba(0,0,0,.06)}

/* === MENTOR === */
.mentor-layout{display:flex;gap:20px}
.mentor-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px;flex:1}
.mentor-card{background:white;border-radius:10px;border:1px solid var(--gray2);overflow:hidden}
.mentor-thumb{height:100px;background:var(--gray2);position:relative;overflow:hidden}
.mentor-thumb img{width:100%;height:100%;object-fit:cover}
.mentor-online{position:absolute;bottom:8px;right:8px;width:10px;height:10px;border-radius:50%;background:#22c55e;border:2px solid white}
.mentor-body{padding:12px}
.mentor-name{font-size:13px;font-weight:700;color:var(--text);margin-bottom:2px}
.mentor-univ{font-size:11px;color:var(--blue2);margin-bottom:2px}
.mentor-dept{font-size:10px;color:var(--gray4);margin-bottom:6px}
.mentor-badges{display:flex;gap:4px;flex-wrap:wrap;margin-bottom:10px}
.badge{font-size:9px;font-weight:600;padding:2px 7px;border-radius:4px;background:var(--gray);color:var(--gray5)}
.mentor-rating{display:flex;align-items:center;gap:4px;font-size:11px;color:var(--gray4);margin-bottom:10px}
.mentor-rating i{color:#f59e0b;font-size:10px}
.btn-profile{width:100%;border:1px solid var(--gray2);background:none;border-radius:6px;padding:7px;font-size:12px;color:var(--gray5);font-weight:600}
.btn-profile:hover{background:var(--blue2);color:white;border-color:var(--blue2)}

/* === PROFILE MENTOR === */
.profile-header{background:linear-gradient(135deg,var(--blue) 0%,var(--blue2) 100%);border-radius:12px;padding:24px;color:white;display:flex;align-items:center;gap:20px;margin-bottom:20px;position:relative}
.profile-photo{width:80px;height:80px;border-radius:12px;object-fit:cover;border:3px solid rgba(255,255,255,.3);background:var(--gray2);display:flex;align-items:center;justify-content:center;font-size:28px;color:rgba(255,255,255,.5);flex-shrink:0;overflow:hidden}
.profile-info h2{font-size:20px;font-weight:700;margin-bottom:4px}
.profile-info .profile-role{font-size:12px;opacity:.8;margin-bottom:10px}
.profile-stats{display:flex;gap:0;position:absolute;right:24px;top:24px;background:rgba(255,255,255,.15);border-radius:10px;overflow:hidden}
.stat-item{padding:12px 16px;text-align:center;border-right:1px solid rgba(255,255,255,.2)}
.stat-item:last-child{border-right:none}
.stat-num{font-size:18px;font-weight:700;display:block}
.stat-label{font-size:10px;opacity:.75}
.profile-actions{display:flex;gap:10px;margin-top:12px}
.btn-consult{background:rgba(255,255,255,.15);border:1px solid rgba(255,255,255,.3);color:white;border-radius:8px;padding:8px 16px;font-size:12px;font-weight:600}
.btn-msg{background:white;color:var(--blue);border:none;border-radius:8px;padding:8px 16px;font-size:12px;font-weight:600}
.section-box{background:white;border-radius:10px;border:1px solid var(--gray2);padding:16px;margin-bottom:14px}
.section-box h3{font-size:13px;font-weight:700;color:var(--text);margin-bottom:10px;display:flex;align-items:center;gap:6px}
.section-box h3 i{color:var(--blue2)}
.about-text{font-size:12px;color:var(--gray4);line-height:1.7}
.skill-chips{display:flex;gap:6px;flex-wrap:wrap;margin-top:8px}
.skill-chip{background:#eff6ff;color:var(--blue2);border:none;border-radius:20px;padding:4px 12px;font-size:11px;font-weight:600}
.review-card{background:#f9fafb;border-radius:8px;padding:10px;margin-bottom:8px;font-size:12px;color:var(--gray4);line-height:1.5;border-left:3px solid var(--blue2)}
.review-meta{display:flex;align-items:center;gap:8px;margin-top:6px}
.review-avatar{width:22px;height:22px;border-radius:50%;background:var(--blue2);display:flex;align-items:center;justify-content:center;font-size:8px;color:white;font-weight:700}
.review-name{font-size:11px;font-weight:600;color:var(--text)}
.course-schedule-item{display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--gray2)}
.course-schedule-item:last-child{border-bottom:none}
.course-schedule-name{font-size:12px;font-weight:600;color:var(--text)}
.course-schedule-time{font-size:10px;color:var(--gray3)}
.contact-list{list-style:none}
.contact-list li{display:flex;align-items:center;gap:8px;font-size:12px;color:var(--blue2);padding:4px 0}
.contact-list li i{color:var(--blue);width:14px}
.avail-bar{background:linear-gradient(90deg,var(--blue2) 0%,#7dd3fc 100%);height:8px;border-radius:4px;margin-top:6px}

/* === EDIT PROFILE & USER PROFILE === */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);display:flex;align-items:center;justify-content:center;z-index:200}
.modal-box{background:white;border-radius:14px;width:500px;max-height:85vh;overflow-y:auto}
.modal-header{background:var(--blue);color:white;padding:20px 24px;border-radius:14px 14px 0 0;display:flex;align-items:center;gap:14px}
.modal-avatar{width:48px;height:48px;border-radius:8px;background:var(--gray2);display:flex;align-items:center;justify-content:center;font-size:20px;color:var(--gray3);border:2px solid rgba(255,255,255,.3)}
.modal-header h3{font-size:16px;font-weight:700}
.modal-header p{font-size:11px;opacity:.7}
.modal-body{padding:20px 24px}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px}
.form-group{margin-bottom:14px}
.form-label{font-size:11px;font-weight:700;color:var(--gray5);margin-bottom:5px;display:block}
.form-input{width:100%;border:1px solid var(--gray2);border-radius:6px;padding:8px 12px;font-size:13px;outline:none;color:var(--text)}
.form-input:focus{border-color:var(--blue2)}
.modal-save{background:var(--blue2);color:white;border:none;border-radius:8px;padding:9px 24px;font-size:13px;font-weight:600;float:right}
.security-section{border-top:1px solid var(--gray2);padding-top:16px;margin-top:8px}
.security-alert{background:#fef3c7;border-radius:8px;padding:10px 12px;display:flex;gap:8px;align-items:flex-start;margin-bottom:14px}
.security-alert i{color:#d97706;font-size:14px;margin-top:1px;flex-shrink:0}
.security-alert p{font-size:11px;color:#92400e;line-height:1.5}
.notif-check{display:flex;align-items:center;gap:8px;font-size:12px;color:var(--gray4);margin-bottom:6px}
.notif-check input{accent-color:var(--blue2)}

/* === USER PROFILE PAGE === */
.user-profile-banner{background:linear-gradient(135deg,var(--blue) 0%,var(--blue2) 100%);border-radius:12px;padding:24px;color:white;margin-bottom:20px;display:flex;align-items:center;gap:20px;position:relative}
.user-banner-photo{width:72px;height:72px;border-radius:50%;background:var(--gray2);border:3px solid rgba(255,255,255,.3);object-fit:cover;display:flex;align-items:center;justify-content:center;font-size:26px;color:rgba(255,255,255,.5);flex-shrink:0;overflow:hidden}
.user-profile-stats{display:flex;gap:24px;margin-top:8px}
.user-stat{text-align:center}
.user-stat-num{font-size:18px;font-weight:700}
.user-stat-label{font-size:10px;opacity:.75}
.user-profile-actions{position:absolute;right:24px;top:24px}
.btn-edit-profile{background:rgba(255,255,255,.15);border:1px solid rgba(255,255,255,.3);color:white;border-radius:8px;padding:8px 16px;font-size:12px;font-weight:600;display:flex;align-items:center;gap:6px}
.profile-two-col{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.activity-item{display:flex;align-items:flex-start;gap:10px;padding:8px 0;border-bottom:1px solid var(--gray2)}
.activity-item:last-child{border-bottom:none}
.activity-dot{width:8px;height:8px;border-radius:50%;background:var(--blue2);flex-shrink:0;margin-top:4px}
.activity-text{font-size:12px;color:var(--text);line-height:1.4}
.activity-time{font-size:10px;color:var(--gray3);margin-top:2px}
.academic-info-grid{display:grid;gap:6px}
.academic-row{display:flex;justify-content:space-between;padding:6px 0;border-bottom:1px solid var(--gray2);font-size:12px}
.academic-row:last-child{border-bottom:none}
.academic-row .label{color:var(--gray4)}
.academic-row .value{font-weight:600;color:var(--text)}
.tracker-item{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--gray2)}
.tracker-item:last-child{border-bottom:none}
.tracker-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.tracker-dot.active{background:#22c55e}
.tracker-dot.pending{background:#f59e0b}
.tracker-dot.inactive{background:var(--gray3)}
.tracker-name{font-size:12px;font-weight:600;color:var(--text)}
.tracker-time{font-size:10px;color:var(--gray3)}
.social-list{list-style:none}
.social-list li{display:flex;align-items:center;gap:8px;font-size:12px;color:var(--blue2);padding:4px 0}
.social-list li i{color:var(--blue);width:14px}

/* === COURSE DETAIL === */
.course-hero{background:linear-gradient(135deg,var(--blue) 0%,#1e40af 100%);border-radius:12px;padding:28px;color:white;margin-bottom:0;border-bottom-left-radius:0;border-bottom-right-radius:0}
.course-hero .back-btn{display:inline-flex;align-items:center;gap:6px;font-size:12px;opacity:.8;margin-bottom:12px;cursor:pointer;background:none;border:none;color:white;padding:0}
.course-hero .back-btn:hover{opacity:1}
.course-hero h2{font-size:22px;font-weight:700}
.course-hero .rating{display:flex;align-items:center;gap:4px;font-size:12px;margin-bottom:8px}
.course-hero .rating i{color:#f59e0b;font-size:11px}
.course-tabs{background:white;border-bottom:1px solid var(--gray2);display:flex;gap:0}
.course-tab{padding:12px 20px;font-size:13px;font-weight:600;color:var(--gray4);border:none;background:none;cursor:pointer;border-bottom:2px solid transparent;transition:all .15s}
.course-tab.active{color:var(--blue2);border-bottom-color:var(--blue2)}
.course-tab:hover:not(.active){color:var(--text)}
.course-content{background:white;border-radius:0 0 12px 12px;border:1px solid var(--gray2);border-top:none;padding:20px}
.about-course-box{background:#f8fafc;border-radius:10px;border:1px solid var(--gray2);padding:16px;margin-bottom:16px}
.about-course-box h4{font-size:13px;font-weight:700;margin-bottom:8px}
.about-course-box p{font-size:12px;color:var(--gray4);line-height:1.7}
.upload-banner{background:#eff6ff;border-radius:10px;border:1px solid #bfdbfe;padding:16px 20px;display:flex;align-items:center;justify-content:space-between;margin-bottom:20px}
.upload-banner-text h4{font-size:13px;font-weight:700;color:var(--text);margin-bottom:2px}
.upload-banner-text p{font-size:11px;color:var(--gray4)}
.btn-upload{background:var(--blue2);color:white;border:none;border-radius:8px;padding:9px 18px;font-size:12px;font-weight:600}
.materials-list{display:flex;flex-direction:column;gap:8px}
.material-item{display:grid;grid-template-columns:1fr auto auto auto auto;gap:12px;align-items:center;padding:12px;background:#fafafa;border-radius:8px;border:1px solid var(--gray2)}
.material-item:hover{background:white;box-shadow:0 2px 6px rgba(0,0,0,.05)}
.material-icon{width:28px;height:28px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0}
.material-icon.pdf{background:#fee2e2;color:#dc2626}
.material-icon.ppt{background:#fef3c7;color:#d97706}
.material-info{display:flex;align-items:center;gap:10px}
.material-name{font-size:12px;font-weight:600;color:var(--text)}
.material-meta{font-size:10px;color:var(--gray3);margin-top:1px;display:flex;gap:10px}
.material-meta span{display:flex;align-items:center;gap:3px}
.btn-download{background:var(--blue2);color:white;border:none;border-radius:6px;padding:6px 14px;font-size:11px;font-weight:600;white-space:nowrap;display:flex;align-items:center;gap:4px}
.mentor-connect-item{display:flex;align-items:center;gap:14px;padding:14px 0;border-bottom:1px solid var(--gray2)}
.mentor-connect-item:last-child{border-bottom:none}
.mentor-connect-photo{width:44px;height:44px;border-radius:50%;background:var(--gray2);display:flex;align-items:center;justify-content:center;font-size:18px;color:var(--gray3);flex-shrink:0;overflow:hidden}
.mentor-connect-name{font-size:13px;font-weight:700;color:var(--text);margin-bottom:2px}
.mentor-connect-dept{font-size:11px;color:var(--gray4)}
.mentor-connect-rating{display:flex;align-items:center;gap:3px;font-size:11px;color:var(--gray4);margin-top:2px}
.mentor-connect-rating i{color:#f59e0b;font-size:10px}
.btn-connect{margin-left:auto;background:var(--blue);color:white;border:none;border-radius:6px;padding:7px 18px;font-size:12px;font-weight:600}
.btn-connect:hover{background:var(--blue3)}

/* === UPLOAD MODAL === */
.upload-modal{background:white;border-radius:12px;width:440px;overflow:hidden}
.upload-modal-header{display:flex;align-items:center;justify-content:space-between;padding:16px 20px;border-bottom:1px solid var(--gray2)}
.upload-modal-header h3{font-size:15px;font-weight:700}
.upload-modal-header button{background:none;border:none;font-size:18px;color:var(--gray3);cursor:pointer}
.upload-drop{border:2px dashed var(--gray2);border-radius:10px;padding:40px;text-align:center;margin:16px;cursor:pointer}
.upload-drop:hover{border-color:var(--blue2);background:#f8faff}
.upload-drop i{font-size:32px;color:var(--gray3);margin-bottom:12px;display:block}
.upload-drop p{font-size:12px;color:var(--gray4);line-height:1.6}
.upload-drop a{color:var(--blue2);font-weight:600}
.upload-drop .formats{font-size:10px;color:var(--gray3);margin-top:6px}
.upload-modal-footer{padding:14px 20px;border-top:1px solid var(--gray2);display:flex;justify-content:flex-end;gap:10px}
.btn-cancel{border:1px solid var(--gray2);background:none;border-radius:6px;padding:8px 18px;font-size:13px;font-weight:500;color:var(--gray4)}
.btn-start-upload{background:var(--blue2);color:white;border:none;border-radius:6px;padding:8px 18px;font-size:13px;font-weight:600}

/* === ASK QUESTION MODAL === */
.ask-modal{background:white;border-radius:12px;width:440px;overflow:hidden}
.ask-modal-header{display:flex;align-items:center;justify-content:space-between;padding:16px 20px;border-bottom:1px solid var(--gray2)}
.ask-modal-header h3{font-size:15px;font-weight:700}
.ask-modal-body{padding:16px 20px}
.ask-textarea{width:100%;border:1px solid var(--gray2);border-radius:8px;padding:12px;font-size:13px;min-height:100px;resize:vertical;outline:none;color:var(--text)}
.ask-textarea:focus{border-color:var(--blue2)}
.ask-attach{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--gray4);padding:8px 12px;border-top:1px solid var(--gray2)}
.ask-attach i{color:var(--gray3)}
.char-count{margin-left:auto}
.ask-tip{display:flex;align-items:flex-start;gap:8px;background:#f0fdf4;border-radius:8px;padding:10px 12px;margin-top:10px}
.ask-tip i{color:#22c55e;font-size:13px;margin-top:1px;flex-shrink:0}
.ask-tip p{font-size:11px;color:#166534;line-height:1.5}
.ask-modal-footer{padding:12px 20px;border-top:1px solid var(--gray2);display:flex;justify-content:center}
.btn-ask-submit{background:var(--blue);color:white;border:none;border-radius:8px;padding:10px 40px;font-size:13px;font-weight:600}
.success-modal{background:white;border-radius:12px;width:320px;padding:32px;text-align:center}
.success-icon{width:56px;height:56px;border-radius:50%;background:#dcfce7;display:flex;align-items:center;justify-content:center;font-size:24px;color:#22c55e;margin:0 auto 14px}
.success-modal h3{font-size:16px;font-weight:700;margin-bottom:6px}
.success-modal p{font-size:12px;color:var(--gray4)}

/* semester card */
.semester-card{background:white;border-radius:10px;border:1px solid var(--gray2);padding:14px;margin-bottom:14px}
.semester-num{font-size:28px;font-weight:700;color:var(--blue);margin-bottom:2px}
.semester-label{font-size:10px;color:var(--gray4);margin-bottom:6px;text-transform:uppercase;letter-spacing:.5px}
.avail-text{font-size:10px;color:var(--gray3)}

/* util */
.badge-verified{background:#dbeafe;color:var(--blue2);font-size:10px;font-weight:700;padding:2px 8px;border-radius:4px;display:inline-flex;align-items:center;gap:4px}
.badge-verified i{font-size:9px}

</style>
</head>
<body>

<!-- ========== LOGIN PAGE ========== -->
<div id="page-login" class="page active">
  <div class="auth-card">
    <div class="auth-icon"><i class="fas fa-user-graduate"></i></div>
    <div class="auth-title">LOGIN</div>
    <label class="auth-label">Email <span>*</span></label>
    <input type="email" class="auth-input" placeholder="Your Email">
    <label class="auth-label">Password <span style="opacity:0">*</span>
      <a href="#" class="forgot">Forgot password?</a>
    </label>
    <div class="pw-wrap">
      <i class="fas fa-lock pw-lock"></i>
      <input type="password" class="auth-input" value="••••••••">
      <i class="fas fa-eye eye"></i>
    </div>
    <button class="auth-btn" onclick="goTo('dashboard')">Sign In →</button>
    <span class="auth-link">Don't have an account? <a href="#" onclick="goTo('register')">Register Account</a></span>
  </div>
</div>

<!-- ========== REGISTER PAGE ========== -->
<div id="page-register" class="page" style="align-items:center;justify-content:center">
  <div class="reg-card">
    <i class="fas fa-graduation-cap reg-bg" aria-hidden="true"></i>
    <div style="text-align:center;margin-bottom:20px">
      <div class="reg-title">Create Account</div>
      <div class="reg-sub">Register to join the Academic Nexus network.</div>
    </div>
    <div class="form-group"><label class="auth-label">Full Name</label><input type="text" class="auth-input" placeholder="Your Name"></div>
    <div class="form-group"><label class="auth-label">Email</label><input type="email" class="auth-input" placeholder="Your Email"></div>
    <div class="reg-row">
      <div><label class="auth-label">Student ID</label><input type="text" class="auth-input" placeholder="Your Student ID"></div>
      <div><label class="auth-label">Major</label>
        <select class="auth-input"><option>Select Major</option><option>Informatika</option><option>Teknologi Informasi</option></select>
      </div>
    </div>
    <div class="form-group"><label class="auth-label">Password</label><input type="password" class="auth-input" value="••••••"></div>
    <div class="form-group"><label class="auth-label">Confirm Password</label><input type="password" class="auth-input" value="••••••"></div>
    <div class="check-row"><input type="checkbox" checked><span>I agree to the <a href="#">Terms of Service</a> and <a href="#">Privacy Policy</a>.</span></div>
    <button class="auth-btn" onclick="goTo('dashboard')">Create Account</button>
    <span class="auth-link">Already have an account? <a href="#" onclick="goTo('login')">Log in</a></span>
  </div>
</div>

<!-- ========== MAIN APP PAGES ========== -->
<!-- Dashboard -->
<div id="page-dashboard" class="page">
  <div class="app-layout">
    <!-- TOPBAR -->
    <div class="topbar">
      <div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div>
      <div class="topbar-actions">
        <i class="fas fa-bell"></i>
        <i class="fas fa-question-circle"></i>
        <div class="avatar" onclick="goTo('user-profile')">PP</div>
      </div>
    </div>
    <div class="main-body">
      <!-- SIDEBAR -->
      <div class="sidebar">
        <div>
          <div class="sidebar-brand">
            <div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div>
            <div>
              <div class="sidebar-brand-text">Academic Portal</div>
              <div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div>
            </div>
          </div>
          <div class="sidebar-section">
            <div class="nav-item active" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> My Courses</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom">
          <div class="nav-item"><i class="fas fa-cog"></i> Settings</div>
          <div class="nav-item"><i class="fas fa-life-ring"></i> Support</div>
        </div>
      </div>
      <!-- CONTENT -->
      <div class="content">
        <div class="welcome-banner">
          <h1>Welcome, Peter Parker</h1>
          <p>Lanjutkan riset kolaboratif Anda. Ada 3 pembaruan penting dalam thread penelitian Anda hari ini.</p>
          <button class="btn-explore" onclick="goTo('research')">Explore Courses</button>
        </div>

        <div class="section-header">
          <div class="section-title">My Courses</div>
          <div class="view-all" onclick="goTo('my-courses')">View All</div>
        </div>
        <div class="courses-row" style="margin-bottom:24px">
          <div class="course-card" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a3a6e,#2563eb)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-square-root-alt"></i></div>
            <div class="course-info">
              <div class="course-rating"><i class="fas fa-star"></i> 5.0</div>
              <div class="course-name">Aljabar Linear & Matriks</div>
              <button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button>
            </div>
          </div>
          <div class="course-card" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1e3a5f,#0369a1)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-database"></i></div>
            <div class="course-info">
              <div class="course-rating"><i class="fas fa-star"></i> 4.8</div>
              <div class="course-name">Pemograman SQL</div>
              <button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button>
            </div>
          </div>
          <div class="course-card" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a3a2e,#15803d)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-code"></i></div>
            <div class="course-info">
              <div class="course-rating"><i class="fas fa-star"></i> 4.5</div>
              <div class="course-name">Pemograman Java</div>
              <button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button>
            </div>
          </div>
          <div class="course-card" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1e2a5e,#4338ca)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-server"></i></div>
            <div class="course-info">
              <div class="course-rating"><i class="fas fa-star"></i> 4.7</div>
              <div class="course-name">Desain Basis Data</div>
              <button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button>
            </div>
          </div>
          <div class="course-card" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#3b1f5e,#7c3aed)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-desktop"></i></div>
            <div class="course-info">
              <div class="course-rating"><i class="fas fa-star"></i> 5.0</div>
              <div class="course-name">Dasar Desain Antar Muka</div>
              <button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button>
            </div>
          </div>
        </div>

        <div class="section-header">
          <div class="section-title"><i class="fas fa-comments" style="color:var(--blue2);margin-right:6px"></i>Discussion</div>
          <div class="view-all" onclick="goTo('discussion')">View All</div>
        </div>
        <div class="discussion-grid">
          <div class="disc-card">
            <div class="disc-user">
              <div class="disc-avatar">OW</div>
              <div><div class="disc-username">Owilll</div><div class="disc-time">Yesterday</div></div>
              <div class="disc-likes"><i class="fas fa-heart"></i> 128</div>
            </div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions">
              <span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span>
              <span class="disc-action"><i class="fas fa-share-alt"></i> Share</span>
            </div>
          </div>
          <div class="disc-card">
            <div class="disc-user">
              <div class="disc-avatar" style="background:#7c3aed">WW</div>
              <div><div class="disc-username">Wowokk</div><div class="disc-time">Yesterday</div></div>
              <div class="disc-likes"><i class="fas fa-heart"></i> 128</div>
            </div>
            <div class="disc-title">Dataset sharing untuk riset keberlanjutan energi di Indonesia</div>
            <div class="disc-body">Rekan-rekan, saya sedang mengumpulkan dataset untuk emisi karbon per perawilayah. Apakah ada yang memiliki akses ke database terbuka selain milik...</div>
            <div class="disc-actions">
              <span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span>
              <span class="disc-action"><i class="fas fa-share-alt"></i> Share</span>
            </div>
          </div>
          <div class="disc-card">
            <div class="disc-user">
              <div class="disc-avatar" style="background:#d97706">AH</div>
              <div><div class="disc-username">Ahilll</div><div class="disc-time">Yesterday</div></div>
              <div class="disc-likes"><i class="fas fa-heart"></i> 128</div>
            </div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions">
              <span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span>
              <span class="disc-action"><i class="fas fa-share-alt"></i> Share</span>
            </div>
          </div>
          <div class="disc-card">
            <div class="disc-user">
              <div class="disc-avatar" style="background:#22c55e">FU</div>
              <div><div class="disc-username">Fufaaaaa</div><div class="disc-time">Yesterday</div></div>
              <div class="disc-likes"><i class="fas fa-heart"></i> 128</div>
            </div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions">
              <span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span>
              <span class="disc-action"><i class="fas fa-share-alt"></i> Share</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- MY COURSES -->
<div id="page-my-courses" class="page">
  <div class="app-layout">
    <div class="topbar">
      <div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div>
      <div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div>
    </div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item active" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> My Courses</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <h2 style="font-size:20px;font-weight:700;margin-bottom:16px">Koleksi Saya</h2>
        <div class="courses-grid">
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a3a6e,#2563eb)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-square-root-alt" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 5.0</div><div class="course-name">Aljabar Linear & Matriks</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1e3a5f,#0369a1)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-database" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.8</div><div class="course-name">Pemograman SQL</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a3a2e,#15803d)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-code" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.5</div><div class="course-name">Pemograman Java</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1e2a5e,#4338ca)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-server" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.7</div><div class="course-name">Desain Basis Data</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#3b1f5e,#7c3aed)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-desktop" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 5.0</div><div class="course-name">Dasar Desain Antar Muka</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#422006,#b45309)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-microchip" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.7</div><div class="course-name">Sistem Operasi</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1c3a1c,#166534)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-chart-bar" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.0</div><div class="course-name">Probabilitas & Statistika</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a2a3a,#0f4c75)"><span class="course-tag">INFORMATIKA</span><i class="fas fa-shield-alt" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 5.0</div><div class="course-name">Keamanan Siber</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
          <div class="course-card-v" onclick="goTo('course-detail')">
            <div class="course-thumb" style="background:linear-gradient(135deg,#1a1a2e,#c0392b)"><span class="course-tag">GENERAL</span><i class="fas fa-flag" style="color:rgba(255,255,255,.7);font-size:22px"></i></div>
            <div class="course-info"><div class="course-rating"><i class="fas fa-star"></i> 4.3</div><div class="course-name">Bahasa Indonesia</div><button class="btn-detail" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
          </div>
        </div>

        <div class="section-header">
          <div class="section-title">Downloaded Materials</div>
          <div class="view-all" style="display:flex;align-items:center;gap:4px"><i class="fas fa-broom" style="font-size:11px"></i> Clean All</div>
        </div>
        <div class="downloads-table">
          <div class="table-header">
            <span>Nama File</span><span>Mata Kuliah</span><span>Ukuran</span><span>Aksi</span>
          </div>
          <div class="table-row">
            <div class="file-info"><div class="file-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="file-name">Modul 01 - ERD to Relasional.pdf</div><div class="file-date">Diunduh 2 jam yang lalu</div></div></div>
            <div class="file-subject">Struktur Data</div>
            <div class="file-size">2.4 MB</div>
            <div class="file-actions"><button class="btn-open">Open</button><i class="fas fa-trash" style="color:var(--gray3);font-size:13px;cursor:pointer"></i></div>
          </div>
          <div class="table-row">
            <div class="file-info"><div class="file-icon ppt"><i class="fas fa-file-powerpoint"></i></div><div><div class="file-name">Lecture Note - Neural Networks.ppt</div><div class="file-date">Diunduh kemarin</div></div></div>
            <div class="file-subject">Kecerdasan Buatan</div>
            <div class="file-size">15.8 MB</div>
            <div class="file-actions"><button class="btn-open">Open</button><i class="fas fa-trash" style="color:var(--gray3);font-size:13px;cursor:pointer"></i></div>
          </div>
          <div class="table-row">
            <div class="file-info"><div class="file-icon doc"><i class="fas fa-file-word"></i></div><div><div class="file-name">Tugas Akhir Semester 2023.docx</div><div class="file-date">Diunduh 3 hari yang lalu</div></div></div>
            <div class="file-subject">Sistem Informasi</div>
            <div class="file-size">840 KB</div>
            <div class="file-actions"><button class="btn-open">Open</button><i class="fas fa-trash" style="color:var(--gray3);font-size:13px;cursor:pointer"></i></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- RESEARCH -->
<div id="page-research" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> Courses</div>
            <div class="nav-item active" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <div style="margin-bottom:6px"><div style="font-size:20px;font-weight:700">Course Exploration</div><div style="font-size:12px;color:var(--gray4);margin-top:2px">Discover the best curriculum designed to prepare you for a professional career in the future</div></div>
        <div style="margin-top:16px;margin-bottom:20px" class="search-bar">
          <input type="text" class="search-input" placeholder="Browse Courses....">
          <button class="btn-search">Search</button>
        </div>
        <div class="research-layout">
          <div class="filter-panel">
            <div class="filter-title">Filter</div>
            <label class="filter-label">FACULTY</label>
            <select class="filter-select"><option>All Faculties</option><option>Fakultas Ilmu Komputer</option></select>
            <label class="filter-label">STUDY PROGRAM</label>
            <select class="filter-select"><option>All Program</option><option>Informatika</option><option>Teknologi Informasi</option></select>
            <button class="btn-search-filter">Search</button>
          </div>
          <div style="flex:1">
            <div class="research-grid">
              <div class="research-card" onclick="goTo('course-detail')">
                <div class="research-thumb" style="background:linear-gradient(135deg,#0f172a,#1e3a8a)"><span class="research-tag">INFORMATIKA</span></div>
                <div class="research-info"><div class="research-rating"><i class="fas fa-star"></i> 5.0</div><div class="research-name">Aljabar Linear & Matriks</div><button class="btn-detail-lg" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
              </div>
              <div class="research-card" onclick="goTo('course-detail')">
                <div class="research-thumb" style="background:linear-gradient(135deg,#0f2027,#1565c0)"><span class="research-tag">INFORMATIKA</span></div>
                <div class="research-info"><div class="research-rating"><i class="fas fa-star"></i> 4.8</div><div class="research-name">Pemograman SQL</div><button class="btn-detail-lg" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
              </div>
              <div class="research-card" onclick="goTo('course-detail')">
                <div class="research-thumb" style="background:linear-gradient(135deg,#0a3d0a,#1a5a1a)"><span class="research-tag">INFORMATIKA</span></div>
                <div class="research-info"><div class="research-rating"><i class="fas fa-star"></i> 4.5</div><div class="research-name">Pemograman Java</div><button class="btn-detail-lg" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
              </div>
              <div class="research-card" onclick="goTo('course-detail')">
                <div class="research-thumb" style="background:linear-gradient(135deg,#1a1a2e,#c0392b)"><span class="research-tag">GENERAL</span></div>
                <div class="research-info"><div class="research-rating"><i class="fas fa-star"></i> 4.3</div><div class="research-name">Bahasa Indonesia</div><button class="btn-detail-lg" onclick="event.stopPropagation();goTo('course-detail')">Detail</button></div>
              </div>
            </div>
            <div class="pagination">
              <button class="page-btn"><i class="fas fa-chevron-left" style="font-size:10px"></i></button>
              <button class="page-btn active">1</button>
              <button class="page-btn">2</button>
              <button class="page-btn">3</button>
              <button class="page-btn">...</button>
              <button class="page-btn">5</button>
              <button class="page-btn"><i class="fas fa-chevron-right" style="font-size:10px"></i></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- DISCUSSION -->
<div id="page-discussion" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> My Courses</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item active" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <div class="discussion-hero">
          <h2>Got Questions?</h2>
          <button class="btn-ask" onclick="showModal('ask-modal')">Ask Now</button>
        </div>
        <div class="filter-tags">
          <span>Active Filters:</span>
          <button class="tag active">#programatik</button>
          <button class="tag active">#implementasikan</button>
        </div>
        <div class="sort-row">
          <span>Sort by</span>
          <select class="sort-select"><option>Most Recent</option><option>Most Popular</option></select>
        </div>
        <div class="disc-list">
          <div class="disc-list-card">
            <div class="disc-user"><div class="disc-avatar">OW</div><div><div class="disc-username">Owilll</div><div class="disc-time">Yesterday</div></div><div class="disc-likes" style="margin-left:auto"><i class="fas fa-heart"></i> 128</div></div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions"><span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span><span class="disc-action"><i class="fas fa-share-alt"></i> Share</span></div>
          </div>
          <div class="disc-list-card">
            <div class="disc-user"><div class="disc-avatar">OW</div><div><div class="disc-username">Owilll</div><div class="disc-time">Yesterday</div></div><div class="disc-likes" style="margin-left:auto"><i class="fas fa-heart"></i> 128</div></div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions"><span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span><span class="disc-action"><i class="fas fa-share-alt"></i> Share</span></div>
          </div>
          <div class="disc-list-card">
            <div class="disc-user"><div class="disc-avatar">OW</div><div><div class="disc-username">Owilll</div><div class="disc-time">Yesterday</div></div><div class="disc-likes" style="margin-left:auto"><i class="fas fa-heart"></i> 128</div></div>
            <div class="disc-title">Rekomendasi software untuk simulasi struktur jembatan bentang panjang?</div>
            <div class="disc-body">Selain SAP2000, apakah ada software lain yang lebih user-friendly untuk analisis beban dinamis pada jembatan gantung? Saya sedang membandingkan akurasi...</div>
            <div class="disc-actions"><span class="disc-action"><i class="fas fa-comment"></i> 15 Answer</span><span class="disc-action"><i class="fas fa-share-alt"></i> Share</span></div>
          </div>
        </div>
        <div class="pagination" style="margin-top:20px">
          <button class="page-btn"><i class="fas fa-chevron-left" style="font-size:10px"></i></button>
          <button class="page-btn active">1</button><button class="page-btn">2</button><button class="page-btn">3</button><button class="page-btn">...</button><button class="page-btn">5</button>
          <button class="page-btn"><i class="fas fa-chevron-right" style="font-size:10px"></i></button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- MENTOR LIST -->
<div id="page-mentor" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> Courses</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item active" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <div class="mentor-layout">
          <div class="filter-panel">
            <div class="filter-title">Filter</div>
            <label class="filter-label">FACULTY</label>
            <select class="filter-select"><option>All Faculties</option><option>Fakultas Ilmu Komputer</option></select>
            <label class="filter-label">STUDY PROGRAM</label>
            <select class="filter-select"><option>All Program</option><option>Informatika</option></select>
            <button class="btn-search-filter">Search</button>
          </div>
          <div style="flex:1">
            <div style="margin-bottom:16px">
              <div class="search-bar">
                <input type="text" class="search-input" placeholder="Browse Mentor Directory...">
                <button class="btn-search">Search</button>
              </div>
            </div>
            <div class="mentor-grid">
              <div class="mentor-card">
                <div class="mentor-thumb" style="background:#e2e8f0;display:flex;align-items:center;justify-content:center"><i class="fas fa-user" style="font-size:36px;color:#94a3b8"></i><div class="mentor-online"></div></div>
                <div class="mentor-body">
                  <div class="mentor-name">Radit Ahmad Maulana</div>
                  <div class="mentor-univ">Universitas Brawijaya</div>
                  <div class="mentor-dept">Fakultas Ilmu Komputer</div>
                  <div class="mentor-badges"><span class="badge">INFORMATION SYS.</span><span class="badge">INFORMATIKA</span></div>
                  <div class="mentor-rating"><i class="fas fa-star"></i> 4.5 · 15 Mentor</div>
                  <button class="btn-profile" onclick="goTo('mentor-profile')">See Profile</button>
                </div>
              </div>
              <div class="mentor-card">
                <div class="mentor-thumb" style="background:#dde4f0;display:flex;align-items:center;justify-content:center"><i class="fas fa-user" style="font-size:36px;color:#94a3b8"></i><div class="mentor-online"></div></div>
                <div class="mentor-body">
                  <div class="mentor-name">Muhammad Reza</div>
                  <div class="mentor-univ">Universitas Brawijaya</div>
                  <div class="mentor-dept">Fakultas Ilmu Komputer</div>
                  <div class="mentor-badges"><span class="badge">INFORMATION SYS.</span><span class="badge">INFORMATIKA</span></div>
                  <div class="mentor-rating"><i class="fas fa-star"></i> 4.8 · 20 Mentor</div>
                  <button class="btn-profile" onclick="goTo('mentor-profile')">See Profile</button>
                </div>
              </div>
              <div class="mentor-card">
                <div class="mentor-thumb" style="background:#e2ece4;display:flex;align-items:center;justify-content:center"><i class="fas fa-user" style="font-size:36px;color:#94a3b8"></i><div class="mentor-online" style="background:#94a3b8"></div></div>
                <div class="mentor-body">
                  <div class="mentor-name">Ginalya Kartika</div>
                  <div class="mentor-univ">Universitas Brawijaya</div>
                  <div class="mentor-dept">Fakultas Ilmu Komputer</div>
                  <div class="mentor-badges"><span class="badge">INFORMATION SYS.</span><span class="badge">TEKNOLOGI INF.</span></div>
                  <div class="mentor-rating"><i class="fas fa-star"></i> 4.9 · 20 Mentor</div>
                  <button class="btn-profile" onclick="goTo('mentor-profile')">See Profile</button>
                </div>
              </div>
              <div class="mentor-card">
                <div class="mentor-thumb" style="background:#ece2e2;display:flex;align-items:center;justify-content:center"><i class="fas fa-user" style="font-size:36px;color:#94a3b8"></i><div class="mentor-online" style="background:#22c55e"></div></div>
                <div class="mentor-body">
                  <div class="mentor-name">Njoni Teddy</div>
                  <div class="mentor-univ">Fakultas Ilmu Komputer</div>
                  <div class="mentor-dept">Teknik Komputer</div>
                  <div class="mentor-badges"><span class="badge">INFORMATION SYS.</span><span class="badge">CLOUD</span></div>
                  <div class="mentor-rating"><i class="fas fa-star"></i> 3.8 · 32 Mentor</div>
                  <button class="btn-profile" onclick="goTo('mentor-profile')">See Profile</button>
                </div>
              </div>
            </div>
            <div class="pagination">
              <button class="page-btn"><i class="fas fa-chevron-left" style="font-size:10px"></i></button>
              <button class="page-btn active">1</button><button class="page-btn">2</button><button class="page-btn">3</button><button class="page-btn">...</button><button class="page-btn">5</button>
              <button class="page-btn"><i class="fas fa-chevron-right" style="font-size:10px"></i></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- MENTOR PROFILE -->
<div id="page-mentor-profile" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> Courses</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item active" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <div class="profile-header">
          <div class="profile-photo"><i class="fas fa-user"></i></div>
          <div class="profile-info">
            <div style="margin-bottom:4px"><span class="badge-verified" style="background:rgba(255,255,255,.2);color:white"><i class="fas fa-check-circle"></i> SENIOR MENTOR</span>&nbsp;&nbsp;<span style="color:rgba(255,255,255,.7);font-size:11px"><i class="fas fa-star" style="color:#f59e0b"></i> 4.5</span></div>
            <h2>Raditya Maulana Ahmad</h2>
            <div class="profile-role">Teknologi Informasi</div>
            <div style="font-size:11px;opacity:.7;display:flex;align-items:center;gap:12px">
              <span><i class="fas fa-university" style="margin-right:4px"></i>Universitas Brawijaya</span>
              <span><i class="fas fa-map-marker-alt" style="margin-right:4px"></i>Malang, Indonesia</span>
            </div>
            <div class="profile-actions">
              <button class="btn-consult">Schedule Consultation</button>
              <button class="btn-msg">Messages</button>
            </div>
          </div>
          <div class="profile-stats">
            <div class="stat-item"><span class="stat-num">15</span><span class="stat-label">Students</span></div>
            <div class="stat-item"><span class="stat-num">2</span><span class="stat-label">Courses</span></div>
          </div>
        </div>
        <div style="display:grid;grid-template-columns:1fr 240px;gap:16px">
          <div>
            <div class="section-box">
              <h3><i class="fas fa-user"></i> About</h3>
              <div class="about-text">Mahasiswa senior yang aktif berkontribusi di Fakultas Ilmu Komputer Universitas Brawijaya. Memiliki pengalaman akademik yang cukup dalam bidang algoritma, berpengalaman menjadi mentor berbagai mahasiswa, serta berbagi insight perkembangan dan teknik-teknik paling mutakhir dalam pengembangan software.</div>
              <div class="skill-chips" style="margin-top:10px">
                <span class="skill-chip">Pemograman Java</span>
                <span class="skill-chip">Pemograman SQL</span>
              </div>
            </div>
            <div class="section-box">
              <h3><i class="fas fa-star"></i> Student Reviews</h3>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px">
                <div class="review-card">"Ricky membantu saya benar-benar dalam memahami konsep dasar tetapi menjelaskan secara lengkap dan detail. Saya sangat senang."<div class="review-meta"><div class="review-avatar">TA</div><div class="review-name">Tomaya · Informatika</div></div></div>
                <div class="review-card">"Tutor menyenangkan bisa membantu saya mulai dari awal. Cukup detail dan tidak terburu-buru menjelaskannya. Saya sangat puas."<div class="review-meta"><div class="review-avatar">ST</div><div class="review-name">Della Taka · Informatika</div></div></div>
              </div>
            </div>
          </div>
          <div>
            <div class="semester-card">
              <div style="font-size:11px;color:var(--gray4);margin-bottom:4px;font-weight:600;text-transform:uppercase;letter-spacing:.5px">Semester</div>
              <div class="semester-num">6</div>
              <div class="avail-bar" style="width:70%"></div>
              <div class="avail-text" style="margin-top:4px">70% Availability</div>
            </div>
            <div class="section-box">
              <h3><i class="fas fa-calendar-alt"></i> Course Schedule</h3>
              <div class="course-schedule-item"><div><div class="course-schedule-name">Pemograman Java</div><div class="course-schedule-time">Wednesday 08:00</div></div><div style="width:8px;height:8px;border-radius:50%;background:#22c55e;margin-top:4px"></div></div>
              <div class="course-schedule-item"><div><div class="course-schedule-name">Pemograman SQL</div><div class="course-schedule-time">Friday 13:00</div></div><div style="width:8px;height:8px;border-radius:50%;background:#22c55e;margin-top:4px"></div></div>
            </div>
            <div class="section-box">
              <h3><i class="fas fa-address-card"></i> Contact & Social</h3>
              <ul class="contact-list">
                <li><i class="fas fa-envelope"></i> Online Consultation: Zoom</li>
                <li><i class="fas fa-book"></i> Personal Review</li>
                <li><i class="fas fa-briefcase"></i> Consultancy: DM</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- USER PROFILE -->
<div id="page-user-profile" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> Courses</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content">
        <div class="user-profile-banner">
          <div class="user-banner-photo"><i class="fas fa-user"></i></div>
          <div style="flex:1">
            <div style="font-size:20px;font-weight:700;margin-bottom:2px">Peter Parker</div>
            <div style="font-size:12px;opacity:.8;margin-bottom:2px">Information Technology &nbsp;·&nbsp; ID: 2651501111001</div>
            <div class="user-profile-stats">
              <div class="user-stat"><div class="user-stat-num">2</div><div class="user-stat-label">GPA Current</div></div>
              <div class="user-stat"><div class="user-stat-num">4.00</div><div class="user-stat-label">GPA</div></div>
              <div class="user-stat"><div class="user-stat-num">21</div><div class="user-stat-label">Credits Passed</div></div>
            </div>
          </div>
          <div class="user-profile-actions">
            <button class="btn-edit-profile" onclick="showModal('edit-profile-modal')"><i class="fas fa-pen"></i> Edit Profil</button>
          </div>
        </div>
        <div class="profile-two-col">
          <div>
            <div class="section-box">
              <h3><i class="fas fa-bolt"></i> Recent Activity</h3>
              <div class="activity-item"><div class="activity-dot"></div><div><div class="activity-text">Submitted Assignment for Pemfor</div><div class="activity-time">2 hours ago</div></div></div>
              <div class="activity-item"><div class="activity-dot" style="background:#22c55e"></div><div><div class="activity-text">Grading by Mentor for ESSP</div><div class="activity-time">4 hours ago</div></div></div>
              <div class="activity-item"><div class="activity-dot" style="background:#f59e0b"></div><div><div class="activity-text">Baca OKD Scheduled</div><div class="activity-time">Yesterday</div></div></div>
            </div>
            <div class="section-box">
              <h3><i class="fas fa-list-check"></i> Course Tracker</h3>
              <div class="tracker-item"><div class="tracker-dot active"></div><div style="flex:1"><div class="tracker-name">Pemograman Java</div><div class="tracker-time">Today, 08:40</div></div></div>
              <div class="tracker-item"><div class="tracker-dot active"></div><div style="flex:1"><div class="tracker-name">Pemograman SQL</div><div class="tracker-time">Today, 11:00</div></div></div>
              <div class="tracker-item"><div class="tracker-dot inactive"></div><div style="flex:1"><div class="tracker-name">Bahasa Indonesia</div><div class="tracker-time">1 day ago</div></div></div>
              <div class="tracker-item"><div class="tracker-dot inactive"></div><div style="flex:1"><div class="tracker-name">Probabilitas Statistika</div><div class="tracker-time">2 days ago</div></div></div>
              <div class="tracker-item"><div class="tracker-dot inactive"></div><div style="flex:1"><div class="tracker-name">Desain Basis Data</div><div class="tracker-time">3 days ago</div></div></div>
            </div>
          </div>
          <div>
            <div class="section-box">
              <h3><i class="fas fa-university"></i> Academic Data</h3>
              <div class="academic-info-grid">
                <div class="academic-row"><span class="label">Universitas</span><span class="value">Universitas Brawijaya</span></div>
                <div class="academic-row"><span class="label">Jurusan</span><span class="value">Fakultas Ilmu Komputer</span></div>
                <div class="academic-row"><span class="label">Program Studi</span><span class="value">S1 Teknologi Informatika</span></div>
                <div class="academic-row"><span class="label">GPA</span><span class="value" style="color:var(--blue2)">4.00</span></div>
                <div class="academic-row"><span class="label">Status</span><span class="value" style="color:#22c55e">Aktif</span></div>
              </div>
            </div>
            <div class="section-box">
              <h3><i class="fas fa-share-alt"></i> Contact & Social</h3>
              <ul class="social-list">
                <li><i class="fas fa-envelope"></i> peterparker@ub.ac.id</li>
                <li><i class="fas fa-phone"></i> +62 812 3456 7890</li>
                <li><i class="fas fa-link"></i> linkedin.com/in/peterparker</li>
              </ul>
            </div>
          </div>
        </div>
        <div style="text-align:center;margin-top:12px">
          <button style="border:1px solid #fee2e2;background:none;color:#dc2626;border-radius:6px;padding:8px 24px;font-size:12px;font-weight:600;cursor:pointer;display:inline-flex;align-items:center;gap:6px" onclick="goTo('login')"><i class="fas fa-sign-out-alt"></i> LEAVE</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- COURSE DETAIL -->
<div id="page-course-detail" class="page">
  <div class="app-layout">
    <div class="topbar"><div class="topbar-logo"><i class="fas fa-infinity"></i> CollegeHub</div><div class="topbar-actions"><i class="fas fa-bell"></i><i class="fas fa-question-circle"></i><div class="avatar" onclick="goTo('user-profile')">PP</div></div></div>
    <div class="main-body">
      <div class="sidebar">
        <div>
          <div class="sidebar-brand"><div class="sidebar-brand-icon"><i class="fas fa-graduation-cap"></i></div><div><div class="sidebar-brand-text">Academic Portal</div><div class="sidebar-brand-sub">COLLABORATIVE ENVIRONMENT</div></div></div>
          <div class="sidebar-section">
            <div class="nav-item" onclick="goTo('dashboard')"><i class="fas fa-th-large"></i> Dashboard</div>
            <div class="nav-item active" onclick="goTo('my-courses')"><i class="fas fa-book-open"></i> My Courses</div>
            <div class="nav-item" onclick="goTo('research')"><i class="fas fa-search"></i> Research</div>
            <div class="nav-item" onclick="goTo('discussion')"><i class="fas fa-comments"></i> Discussion</div>
            <div class="nav-item" onclick="goTo('mentor')"><i class="fas fa-users"></i> Mentor</div>
          </div>
        </div>
        <div class="sidebar-bottom"><div class="nav-item"><i class="fas fa-cog"></i> Settings</div><div class="nav-item"><i class="fas fa-life-ring"></i> Support</div></div>
      </div>
      <div class="content" style="padding:0">
        <div class="course-hero">
          <button class="back-btn" onclick="goTo('my-courses')"><i class="fas fa-arrow-left"></i> Return</button>
          <div class="rating"><i class="fas fa-star"></i> 4.3</div>
          <h2>Struktur Data dan Algoritma</h2>
        </div>
        <div class="course-tabs" id="course-tabs">
          <button class="course-tab active" onclick="switchCourseTab('overview',this)">Overview</button>
          <button class="course-tab" onclick="switchCourseTab('material',this)">Material</button>
          <button class="course-tab" onclick="switchCourseTab('mentor',this)">Mentor</button>
        </div>
        <div class="course-content">
          <!-- OVERVIEW TAB -->
          <div id="tab-overview">
            <div class="about-course-box">
              <h4>About This Course</h4>
              <p>Mata kuliah Struktur Data dan Algoritma dirancang untuk membekali mahasiswa dengan pemahaman mendalam tentang bagaimana data diorganisasi, dikelola, dan diproses secara efisien dalam sistem komputer.</p>
            </div>
            <div class="upload-banner">
              <div class="upload-banner-text">
                <h4>Have Extra Learning Materials?</h4>
                <p>Help your friends better understand Data Structures with shared notes or practice problems.</p>
              </div>
              <button class="btn-upload" onclick="showModal('upload-modal')">Upload Material</button>
            </div>
            <div class="section-header"><div class="section-title">Materials List</div><div class="view-all" onclick="switchCourseTab('material',document.querySelectorAll('.course-tab')[1])">View All</div></div>
            <div class="materials-list">
              <div class="material-item">
                <div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Modul 1 - Pengenalan Struktur Data</div><div class="material-meta"><span><i class="fas fa-user"></i> A Peter Parker</span><span><i class="fas fa-calendar"></i> 12 Okt 2023</span><span>2.4 MB</span><span>1,204 kali</span></div></div></div>
                <button class="btn-download"><i class="fas fa-download"></i> Download</button>
              </div>
              <div class="material-item">
                <div class="material-info"><div class="material-icon ppt"><i class="fas fa-file-powerpoint"></i></div><div><div class="material-name">Latihan Soal - Linked List & Arrays</div><div class="material-meta"><span><i class="fas fa-user"></i> A fuluhiyela</span><span><i class="fas fa-calendar"></i> 15 Nov 2023</span><span>880 KB</span><span>4,458 kali</span></div></div></div>
                <button class="btn-download"><i class="fas fa-download"></i> Download</button>
              </div>
              <div class="material-item">
                <div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Materi 4 - If else</div><div class="material-meta"><span><i class="fas fa-user"></i> A Wiwok</span><span><i class="fas fa-calendar"></i> 22 Nov 2023</span><span>34 KB</span><span>4,105 kali</span></div></div></div>
                <button class="btn-download"><i class="fas fa-download"></i> Download</button>
              </div>
            </div>
          </div>
          <!-- MATERIAL TAB -->
          <div id="tab-material" style="display:none">
            <div class="section-header" style="margin-bottom:16px">
              <div class="section-title">Materials List</div>
              <input type="text" style="border:1px solid var(--gray2);border-radius:6px;padding:6px 12px;font-size:12px;outline:none" placeholder="Search by name...">
            </div>
            <div class="materials-list">
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Modul 1 - Pengenalan Struktur Data</div><div class="material-meta"><span><i class="fas fa-user"></i> A Rezt Annaz</span><span><i class="fas fa-calendar"></i> 12 Okt 2023</span><span>2.4 MB</span><span>1,204 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Modul 2 - Sistem OBE Aljabar</div><div class="material-meta"><span><i class="fas fa-user"></i> A Mon. Neeru</span><span><i class="fas fa-calendar"></i> 12 Okt 2023</span><span>2.6 MB</span><span>1,256 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon ppt"><i class="fas fa-file-powerpoint"></i></div><div><div class="material-name">Latihan Soal - Linked List & Arrays</div><div class="material-meta"><span><i class="fas fa-user"></i> A fuluhiyela</span><span><i class="fas fa-calendar"></i> 15 Nov 2023</span><span>880 KB</span><span>4,458 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon ppt"><i class="fas fa-file-powerpoint"></i></div><div><div class="material-name">Latihan Soal - Probabilitas & Statistika</div><div class="material-meta"><span><i class="fas fa-user"></i> A Mayor Teddy</span><span><i class="fas fa-calendar"></i> 23 Nov 2023</span><span>679 KB</span><span>4,999 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon ppt"><i class="fas fa-file-powerpoint"></i></div><div><div class="material-name">Latihan Soal - Desain Basis Data</div><div class="material-meta"><span><i class="fas fa-user"></i> A Mega Ulrik</span><span><i class="fas fa-calendar"></i> 23 Sept 2023</span><span>730 KB</span><span>4,109 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Materi 1 - If else</div><div class="material-meta"><span><i class="fas fa-user"></i> A Wiwok</span><span><i class="fas fa-calendar"></i> 22 Nov 2023</span><span>34 KB</span><span>4,105 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Materi 4 - Dasar Desain Antar Pengguna</div><div class="material-meta"><span><i class="fas fa-user"></i> A Jaggan</span><span><i class="fas fa-calendar"></i> 28 Apr 2023</span><span>22 KB</span><span>4.86 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Materi 3 - Kalkulus</div><div class="material-meta"><span><i class="fas fa-user"></i> A Ever</span><span><i class="fas fa-calendar"></i> 21 Nov 2023</span><span>20 KB</span><span>2.75 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
              <div class="material-item"><div class="material-info"><div class="material-icon pdf"><i class="fas fa-file-pdf"></i></div><div><div class="material-name">Materi 4 - Inheritance</div><div class="material-meta"><span><i class="fas fa-user"></i> A Sapri</span><span><i class="fas fa-calendar"></i> 13 Apr 2023</span><span>48 KB</span><span>6.67 kali</span></div></div></div><button class="btn-download"><i class="fas fa-download"></i> Download</button></div>
            </div>
          </div>
          <!-- MENTOR TAB -->
          <div id="tab-mentor" style="display:none">
            <div style="font-size:12px;color:var(--gray4);margin-bottom:12px;display:flex;align-items:center;gap:6px"><i class="fas fa-arrow-left"></i> Kembali ke Beranda</div>
            <div class="mentor-connect-item">
              <div class="mentor-connect-photo"><i class="fas fa-user"></i></div>
              <div><div class="mentor-connect-name">Mayor Teddy</div><div class="mentor-connect-dept">Universitas Brawijaya</div><div class="mentor-connect-rating"><i class="fas fa-star"></i> 4.9 · 44 reviews</div></div>
              <button class="btn-connect" onclick="goTo('mentor-profile')">Connect</button>
            </div>
            <div class="mentor-connect-item">
              <div class="mentor-connect-photo"><i class="fas fa-user"></i></div>
              <div><div class="mentor-connect-name">Puan Maharani</div><div class="mentor-connect-dept">Universitas Brawijaya</div><div class="mentor-connect-rating"><i class="fas fa-star"></i> 4.9 · 68 reviews</div></div>
              <button class="btn-connect" onclick="goTo('mentor-profile')">Connect</button>
            </div>
            <div class="mentor-connect-item">
              <div class="mentor-connect-photo"><i class="fas fa-user"></i></div>
              <div><div class="mentor-connect-name">Donald Trump</div><div class="mentor-connect-dept">Universitas Brawijaya</div><div class="mentor-connect-rating"><i class="fas fa-star"></i> 5.0 · 44 reviews</div></div>
              <button class="btn-connect" onclick="goTo('mentor-profile')">Connect</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ========== MODALS ========== -->
<!-- Upload Modal -->
<div id="upload-modal" class="modal-overlay" style="display:none" onclick="if(event.target===this)hideModal('upload-modal')">
  <div class="upload-modal">
    <div class="upload-modal-header"><h3>Upload Materials</h3><button onclick="hideModal('upload-modal')">×</button></div>
    <div class="upload-drop">
      <i class="fas fa-cloud-upload-alt"></i>
      <p>Drop your files here or <a href="#">Click to browse</a></p>
      <div class="formats">Supports PDF, DOCX, PPTx (Max 50MB per file)</div>
    </div>
    <div class="upload-modal-footer">
      <button class="btn-cancel" onclick="hideModal('upload-modal')">Cancel</button>
      <button class="btn-start-upload" onclick="hideModal('upload-modal')">Start Upload</button>
    </div>
  </div>
</div>

<!-- Ask Question Modal -->
<div id="ask-modal" class="modal-overlay" style="display:none" onclick="if(event.target===this)hideModal('ask-modal')">
  <div class="ask-modal">
    <div class="ask-modal-header"><h3>Ask a Question</h3><button onclick="hideModal('ask-modal')" style="background:none;border:none;font-size:18px;color:var(--gray3);cursor:pointer">×</button></div>
    <div class="ask-modal-body">
      <textarea class="ask-textarea" placeholder="Write your question here (min. 20 characters)..."></textarea>
      <div class="ask-attach"><i class="fas fa-paperclip"></i> Attachments<span class="char-count">0/500</span></div>
      <div class="ask-tip"><i class="fas fa-lightbulb"></i><p>Clear and specific questions are more likely to receive high-quality answers from mentors and fellow students.</p></div>
    </div>
    <div class="ask-modal-footer">
      <button class="btn-ask-submit" onclick="hideModal('ask-modal');showModal('success-modal')">ASK YOUR QUESTION</button>
    </div>
  </div>
</div>

<!-- Success Modal -->
<div id="success-modal" class="modal-overlay" style="display:none" onclick="if(event.target===this)hideModal('success-modal')">
  <div class="success-modal">
    <div class="success-icon"><i class="fas fa-check"></i></div>
    <h3>Question Submitted!</h3>
    <p>Your question has been successfully published on the forum.</p>
    <button class="auth-btn" style="margin-top:20px" onclick="hideModal('success-modal')">Done</button>
  </div>
</div>

<!-- Edit Profile Modal -->
<div id="edit-profile-modal" class="modal-overlay" style="display:none" onclick="if(event.target===this)hideModal('edit-profile-modal')">
  <div class="modal-box">
    <div class="modal-header">
      <div class="modal-avatar"><i class="fas fa-user"></i></div>
      <div><h3>Peter Parker</h3><p>Information Technology · ID: 2651501111001</p></div>
    </div>
    <div class="modal-body">
      <div style="font-size:12px;font-weight:700;color:var(--gray4);margin-bottom:12px;display:flex;align-items:center;gap:6px"><i class="fas fa-id-card"></i> Personal Information</div>
      <div class="form-row">
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Full Name</label><input type="text" class="form-input" value="Peter Parker"></div>
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Student ID Number</label><input type="text" class="form-input" value="2651501111001"></div>
      </div>
      <div class="form-row" style="margin-top:12px">
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Email</label><input type="email" class="form-input" value="peterparker@ub.ac.id"></div>
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Phone Number</label><input type="text" class="form-input" value="+62 812 3456 7900"></div>
      </div>
      <div class="form-row" style="margin-top:12px">
        <div class="form-group" style="margin-bottom:0"><label class="form-label">College</label><input type="text" class="form-input" value="Universitas Brawijaya"></div>
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Major</label><input type="text" class="form-input" value="Information Technology"></div>
      </div>
      <div class="form-row" style="margin-top:12px">
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Semester</label><input type="text" class="form-input" value="3"></div>
        <div class="form-group" style="margin-bottom:0"><label class="form-label">Credits Passed</label><input type="text" class="form-input" value="51"></div>
      </div>
      <div class="form-row" style="margin-top:12px;margin-bottom:4px">
        <div class="form-group" style="margin-bottom:0"><label class="form-label">GPA</label><input type="text" class="form-input" value="4.80"></div>
        <div style="display:flex;align-items:flex-end"><button class="modal-save" onclick="hideModal('edit-profile-modal')">Save</button></div>
      </div>
      <div class="security-section">
        <div style="font-size:12px;font-weight:700;color:var(--gray4);margin-bottom:10px;display:flex;align-items:center;gap:6px"><i class="fas fa-shield-alt"></i> Security</div>
        <div class="security-alert"><i class="fas fa-exclamation-triangle"></i><p>Your password was not changed 5 months ago, use a combination of letters, numbers, and symbols for maximum security.</p></div>
        <div class="form-row">
          <div class="form-group" style="margin-bottom:0"><label class="form-label">New Password</label><input type="password" class="form-input" value="••••••"></div>
          <div class="form-group" style="margin-bottom:0"><label class="form-label">Confirm Password</label><input type="password" class="form-input" value="••••••"></div>
        </div>
        <div style="margin-top:12px;margin-bottom:14px">
          <div class="notif-check"><input type="checkbox" checked> Notifications</div>
          <div class="notif-check"><input type="checkbox" checked> Academic Update</div>
          <div class="notif-check"><input type="checkbox"> Email Notification</div>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:center">
          <button class="auth-btn" style="width:auto;padding:8px 20px;font-size:12px" onclick="hideModal('edit-profile-modal')">Update Password</button>
          <button style="border:none;background:none;color:#dc2626;font-size:12px;cursor:pointer;font-weight:600;display:flex;align-items:center;gap:4px" onclick="goTo('login')"><i class="fas fa-sign-out-alt"></i> LEAVE</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
function goTo(page){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  const el=document.getElementById('page-'+page);
  if(el){el.classList.add('active');el.scrollTop=0;window.scrollTo(0,0)}
}
function showModal(id){document.getElementById(id).style.display='flex'}
function hideModal(id){document.getElementById(id).style.display='none'}
function switchCourseTab(tab,btn){
  document.querySelectorAll('#tab-overview,#tab-material,#tab-mentor').forEach(t=>t.style.display='none');
  document.getElementById('tab-'+tab).style.display='block';
  document.querySelectorAll('.course-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
}
</script>
</body>
</html>
