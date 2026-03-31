# Suno Music Generation API

Suno AI music and lyrics generation service.

![Platform](https://img.shields.io/badge/platform-Ace%20Data%20Cloud-0f766e?style=flat-square) ![API](https://img.shields.io/badge/type-AI%20API-2563eb?style=flat-square) ![Docs](https://img.shields.io/badge/docs-online-16a34a?style=flat-square)

![Suno Music Generation](https://cdn.acedata.cloud/20240403-192358.png/thumb_600x300)

API home page: [Ace Data Cloud - Suno Music Generation](https://platform.acedata.cloud/service/suno)

Keywords: suno-api, ai-music, music-generation, lyrics-generation, rest-api, ai-api, aiaudio, AI API, REST API, Developer API, Ace Data Cloud

## Why Use Suno Music Generation on Ace Data Cloud

- Unified developer platform with one API key, billing system, and usage tracking
- Production-ready AI API endpoints served from [https://api.acedata.cloud](https://api.acedata.cloud)
- English integration guides, API references, and service documentation
- Global-ready workflow for developers building chat, image, video, music, and search products

## Overview

<style>
.suno-page * { box-sizing: border-box; }
.suno-page h1, .suno-page h2, .suno-page h3, .suno-page h4, .suno-page h5, .suno-page h6, .suno-page p, .suno-page ul, .suno-page ol, .suno-page li, .suno-page pre, .suno-page blockquote, .suno-page table, .suno-page td, .suno-page th { margin: 0; padding: 0; }
.suno-page {
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
color: var(--el-text-color-primary);
background: var(--el-bg-color);
line-height: 1.6;
}
.suno-page a { text-decoration: none; color: inherit; }
.suno-page a:hover { text-decoration: none; }
.suno-page ul { list-style: none; }
.markdown-body .suno-page a { color: inherit !important; text-decoration: none !important; }
.markdown-body .suno-page a:hover { text-decoration: none !important; }
.markdown-body .suno-page a.s-btn-primary,
.markdown-body .suno-page a.price-btn-fill,
.markdown-body .suno-page a.btn-cta-light { color: #ffffff !important; }
.markdown-body .suno-page a.s-btn-secondary { color: var(--el-text-color-primary) !important; }
.markdown-body .suno-page a.price-btn-out { color: var(--el-text-color-primary) !important; }
.markdown-body .suno-page a.btn-cta-ghost { color: #94a3b8 !important; }
.markdown-body .suno-page a.btn-cta-ghost:hover { color: #e2e8f0 !important; }
.markdown-body .suno-page h1, .markdown-body .suno-page h2 { border-bottom: none !important; padding-bottom: 0 !important; }
.s-container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }
.s-container-narrow { max-width: 800px; margin: 0 auto; padding: 0 24px; }
.s-container-wide { max-width: 1100px; margin: 0 auto; padding: 0 32px; }
.s-section { padding: 80px 0; }
.s-section-lg { padding: 100px 0; }
.s-section-sm { padding: 48px 0; }
.s-bg-white { background: var(--el-bg-color); }
.s-bg-gray { background: var(--el-bg-color-page); }
.s-bg-dark { background: #0f172a; color: #f8fafc; }
.s-header { text-align: center; margin-bottom: 64px; }
.s-header h2 {
font-size: clamp(28px, 4vw, 40px);
font-weight: 700;
color: var(--el-text-color-primary);
letter-spacing: normal;
margin-bottom: 20px;
line-height: 1.15;
}
.s-header p {
font-size: clamp(16px, 2vw, 18px);
color: var(--el-text-color-regular);
max-width: 640px;
margin: 0 auto;
line-height: 1.6;
}
.s-bg-dark .s-header h2 { color: #f8fafc; }
.s-bg-dark .s-header p { color: var(--el-text-color-secondary); }
.suno-page .s-btn-primary {
display: inline-flex; align-items: center; gap: 6px;
padding: 14px 28px;
background: #277186; color: #ffffff !important;
border-radius: 9999px; font-size: 15px; font-weight: 600;
transition: background 0.2s, transform 0.15s;
border: none; cursor: pointer;
text-decoration: none !important;
}
.suno-page .s-btn-primary:hover { background: #1f5a6b; transform: translateY(-1px); text-decoration: none !important; }
.suno-page .s-btn-secondary {
display: inline-flex; align-items: center; gap: 6px;
padding: 14px 28px;
background: var(--el-bg-color); color: var(--el-text-color-primary) !important;
border: 1px solid var(--el-border-color-light);
border-radius: 9999px; font-size: 15px; font-weight: 600;
transition: border-color 0.2s, background 0.2s;
cursor: pointer;
text-decoration: none !important;
}
.suno-page .s-btn-secondary:hover { background: var(--el-bg-color-page); text-decoration: none !important; }
.suno-hero {
padding: 100px 0 80px;
text-align: center;
background: var(--el-bg-color);
position: relative;
overflow: hidden;
}
.suno-hero::before {
content: '';
position: absolute;
top: -200px; left: 50%;
transform: translateX(-50%);
width: 900px; height: 500px;
background: radial-gradient(ellipse, rgba(39, 113, 134, 0.06) 0%, transparent 70%);
pointer-events: none;
}
.hero-badge {
display: inline-flex; align-items: center; gap: 8px;
padding: 6px 16px;
background: var(--el-bg-color-page); border: 1px solid var(--el-border-color-light);
border-radius: 9999px; font-size: 13px; font-weight: 600; color: var(--el-text-color-regular);
margin-bottom: 28px;
}
.hero-badge .badge-dot {
width: 6px; height: 6px; background: #10b981; border-radius: 50%;
display: inline-block;
}
.suno-hero h1 {
font-size: clamp(36px, 5vw, 60px);
font-weight: 700; line-height: 1.05;
letter-spacing: normal; color: var(--el-text-color-primary);
margin-bottom: 20px;
position: relative;
}
.suno-hero h1 span { color: #277186; }
.suno-page .hero-subtitle {
font-size: clamp(16px, 2vw, 20px);
color: var(--el-text-color-regular); line-height: 1.6;
max-width: 620px; margin: 0 auto 56px;
position: relative;
}
.hero-actions {
display: flex; gap: 12px; justify-content: center;
flex-wrap: wrap; margin-bottom: 56px; position: relative;
}
.hero-highlights {
display: flex; align-items: center; justify-content: center;
gap: 16px; flex-wrap: wrap; position: relative;
}
.hero-highlights .h-item { font-size: 14px; color: var(--el-text-color-regular); font-weight: 500; }
.hero-highlights .h-div { width: 1px; height: 16px; background: var(--el-border-color-light); }
@media (max-width: 640px) {
.hero-highlights .h-div { display: none; }
.hero-highlights { gap: 8px 16px; }
.hero-actions { flex-direction: column; align-items: center; }
.hero-actions a { width: 100%; max-width: 280px; justify-content: center; }
}
.suno-stats {
padding: 48px 0;
background: var(--el-bg-color-page);
border-top: 1px solid var(--el-border-color-lighter);
border-bottom: 1px solid var(--el-border-color-lighter);
}
.stats-grid {
display: grid; grid-template-columns: repeat(4, 1fr);
gap: 32px; text-align: center;
}
.stat-icon { font-size: 28px; margin-bottom: 12px; }
.stat-val {
font-size: clamp(28px, 4vw, 40px);
font-weight: 700; color: var(--el-text-color-primary);
letter-spacing: normal; margin-bottom: 4px;
}
.stat-lbl { font-size: 14px; color: var(--el-text-color-secondary); font-weight: 500; }
@media (max-width: 768px) { .stats-grid { grid-template-columns: repeat(2, 1fr); gap: 24px; } } @media (max-width: 480px) { .stats-grid { grid-template-columns: 1fr; gap: 20px; } }
.features-grid {
display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px;
}
.feat-card {
padding: 32px 28px;
border: none; border-radius: 20px; box-shadow: 0 2px 12px 0 rgba(0,0,0,0.08);
background: var(--el-bg-color);
transition: border-color 0.2s, box-shadow 0.2s, transform 0.15s;
}
.feat-card:hover { box-shadow: 0 8px 24px 0 rgba(0,0,0,0.12);
transform: translateY(-2px);
}
.feat-icon { font-size: 32px; margin-bottom: 16px; }
.feat-card h3 { font-size: 18px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 8px; }
.feat-card p { font-size: 15px; color: var(--el-text-color-regular); line-height: 1.6; }
@media (max-width: 1024px) { .features-grid { grid-template-columns: repeat(2, 1fr); } } @media (max-width: 640px) { .features-grid { grid-template-columns: 1fr; } } .code-split {
display: flex; gap: 48px; align-items: center;
}
.code-left { flex: 1; min-width: 0; }
.code-right { flex: 1; }
.code-wrap {
border-radius: 16px !important; overflow: hidden !important;
border: 1px solid #334155 !important; background: #0f172a !important;
}
.markdown-body .suno-page .code-wrap {
border-radius: 16px !important; overflow: hidden !important;
border: 1px solid #334155 !important; background: #0f172a !important;
}
.code-bar {
display: flex !important; align-items: center !important; justify-content: space-between !important;
padding: 12px 20px !important; background: #1e293b !important;
border-bottom: 1px solid #334155 !important;
}
.code-dots { display: flex; gap: 6px; }
.code-dots i {
width: 10px; height: 10px; border-radius: 50%;
display: inline-block;
}
.code-dots .r { background: #ef4444; }
.code-dots .y { background: #f59e0b; }
.code-dots .g { background: #10b981; }
.code-lang {
font-size: 12px; color: var(--el-text-color-secondary); font-weight: 600;
text-transform: uppercase; letter-spacing: 0.05em;
}
.code-block {
padding: 24px !important; margin: 0 !important; overflow-x: auto !important;
font-family: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace !important;
font-size: 13.5px !important; line-height: 1.7 !important; color: #e2e8f0 !important;
white-space: pre !important; background: transparent !important;
border: none !important; border-radius: 0 !important;
}
.markdown-body .suno-page .code-block {
padding: 24px !important; margin: 0 !important; overflow-x: auto !important;
font-family: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace !important;
font-size: 13.5px !important; line-height: 1.7 !important; color: #e2e8f0 !important;
white-space: pre !important; background: transparent !important;
border: none !important; border-radius: 0 !important;
}
.code-right h2 {
font-size: clamp(24px, 3vw, 32px);
font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 12px;
letter-spacing: normal;
}
.code-right > p { font-size: 16px; color: var(--el-text-color-regular); line-height: 1.6; margin-bottom: 32px; }
.explain-steps { display: flex; flex-direction: column; gap: 20px; }
.explain-step { display: flex; gap: 16px; align-items: flex-start; }
.step-num {
width: 32px; height: 32px; border-radius: 50%;
background: var(--el-bg-color-page); border: 1px solid var(--el-border-color-light);
display: flex; align-items: center; justify-content: center;
font-size: 14px; font-weight: 700; color: var(--el-text-color-regular);
flex-shrink: 0;
}
.step-text h4 { font-size: 15px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 2px; }
.step-text p { font-size: 14px; color: var(--el-text-color-secondary); line-height: 1.5; }
@media (max-width: 768px) {
.code-split { flex-direction: column; }
.code-left { order: 2; }
.code-right { order: 1; }
} .actions-grid {
display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px;
}
.act-card {
padding: 28px 24px; background: var(--el-bg-color);
border: none; border-radius: 20px; box-shadow: 0 2px 12px 0 rgba(0,0,0,0.08);
text-align: center;
transition: border-color 0.2s, box-shadow 0.2s, transform 0.15s;
}
.act-card:hover { box-shadow: 0 8px 24px 0 rgba(0,0,0,0.12);
transform: translateY(-2px);
}
.act-icon { font-size: 36px; margin-bottom: 16px; }
.act-card h3 { font-size: 17px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 8px; }
.act-card p { font-size: 14px; color: var(--el-text-color-regular); line-height: 1.6; }
@media (max-width: 1024px) { .actions-grid { grid-template-columns: repeat(2, 1fr); } } @media (max-width: 480px) { .actions-grid { grid-template-columns: 1fr; } } .usecases-grid {
display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px;
}
.uc-card {
padding: 28px 24px; background: var(--el-bg-color);
border: none; border-radius: 20px; box-shadow: 0 2px 12px 0 rgba(0,0,0,0.08);
text-align: center;
transition: border-color 0.2s, box-shadow 0.2s, transform 0.15s;
}
.uc-card:hover { box-shadow: 0 8px 24px 0 rgba(0,0,0,0.12);
transform: translateY(-2px);
}
.uc-icon { font-size: 36px; margin-bottom: 16px; }
.uc-card h3 { font-size: 17px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 8px; }
.uc-card p { font-size: 14px; color: var(--el-text-color-regular); line-height: 1.6; }
@media (max-width: 1024px) { .usecases-grid { grid-template-columns: repeat(2, 1fr); } } @media (max-width: 480px) { .usecases-grid { grid-template-columns: 1fr; } }
.steps-row {
display: flex; align-items: flex-start; justify-content: center;
margin-bottom: 48px;
}
.stp-card { flex: 1; max-width: 320px; text-align: center; padding: 0 24px; }
.stp-num {
font-size: clamp(48px, 6vw, 72px);
font-weight: 700; color: #e2e8f0;
letter-spacing: -0.04em; line-height: 1;
margin-bottom: 20px;
}
.stp-card h3 { font-size: 18px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 10px; }
.stp-card p { font-size: 15px; color: var(--el-text-color-regular); line-height: 1.6; }
.stp-conn {
width: 60px; height: 2px; background: var(--el-border-color-light);
margin-top: 36px; flex-shrink: 0;
}
.steps-cta { text-align: center; }
@media (max-width: 768px) {
.steps-row { flex-direction: column; align-items: center; gap: 32px; }
.stp-conn { width: 2px; height: 32px; margin: 0; }
.stp-card { max-width: 100%; }
} .cmp-wrap { overflow-x: auto; -webkit-overflow-scrolling: touch; }
.suno-page .cmp-table {
display: table !important;
width: 100%; max-width: 860px; margin: 0 auto;
border-collapse: collapse; font-size: 15px;
}
.suno-page .cmp-table th, .cmp-table td {
padding: 16px 20px; text-align: center;
border-bottom: 1px solid var(--el-border-color-light);
}
.suno-page .cmp-table th {
font-weight: 700; color: var(--el-text-color-regular); font-size: 14px;
text-transform: uppercase; letter-spacing: 0.04em;
background: var(--el-bg-color-page);
}
.suno-page .cmp-table td:first-child, .cmp-table th:first-child {
text-align: left; font-weight: 600; color: var(--el-text-color-primary);
}
.cmp-us { font-weight: 700; }
.cmp-brand { font-weight: 700; color: var(--el-text-color-primary); }
.ck { color: #10b981; font-weight: 700; font-size: 18px; }
.cx { color: #d1d5db; font-weight: 700; font-size: 18px; }
@media (max-width: 640px) {
.cmp-table th, .cmp-table td { padding: 12px 10px; font-size: 13px; }
} .models-grid {
display: grid; grid-template-columns: repeat(3, 1fr);
gap: 24px; max-width: 960px; margin: 0 auto;
}
.mdl-card {
padding: 32px 28px;
border: none; border-radius: 20px; box-shadow: 0 2px 12px 0 rgba(0,0,0,0.08);
background: var(--el-bg-color); position: relative;
}
.mdl-card.mdl-rec { border-color: #277186; border-width: 2px; }
.mdl-rec-badge {
position: absolute; top: -12px; left: 50%;
transform: translateX(-50%);
padding: 4px 14px; background: #277186; color: #ffffff;
border-radius: 9999px; font-size: 12px; font-weight: 700;
text-transform: uppercase; letter-spacing: 0.04em;
}
.mdl-head { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
.mdl-head h3 { font-size: 20px; font-weight: 700; color: var(--el-text-color-primary); }
.mdl-tag {
padding: 3px 10px; background: var(--el-bg-color-page); border-radius: 9999px;
font-size: 11px; font-weight: 700; color: var(--el-text-color-regular);
text-transform: uppercase; letter-spacing: 0.04em;
}
.mdl-tag-blue { background: #eff6ff; color: #2563eb; }
.mdl-tag-purple { background: #e9f1f3; color: #277186; }
.suno-page .mdl-desc { font-size: 15px; color: var(--el-text-color-regular); line-height: 1.6; margin-bottom: 20px; }
.mdl-feats { display: flex; flex-direction: column; gap: 8px; }
.mdl-feats li { font-size: 14px; color: var(--el-text-color-regular); line-height: 1.4; }
@media (max-width: 768px) { .models-grid { grid-template-columns: 1fr; } } .price-grid {
display: grid !important; grid-template-columns: repeat(2, 1fr) !important;
gap: 24px !important; max-width: 720px !important; margin: 0 auto !important;
align-items: start;
}
.price-card {
padding: 36px 32px;
border: 1px solid var(--el-border-color-light); border-radius: 20px;
background: var(--el-bg-color); position: relative;
}
.price-card-feat {
border: 2px solid #277186;
box-shadow: 0 8px 32px rgba(0,0,0,0.08);
transform: scale(1.03);
}
.price-feat-badge {
position: absolute; top: -13px; left: 50%;
transform: translateX(-50%);
padding: 5px 18px; background: #277186; color: #ffffff;
border-radius: 9999px; font-size: 12px; font-weight: 700;
text-transform: uppercase; letter-spacing: 0.04em;
white-space: nowrap;
}
.price-tier {
font-size: 16px; font-weight: 700; color: var(--el-text-color-regular);
text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 12px;
}
.price-amt {
font-size: clamp(36px, 5vw, 48px);
font-weight: 700; color: var(--el-text-color-primary); letter-spacing: normal;
}
.price-per { font-size: 16px; color: var(--el-text-color-secondary); font-weight: 500; }
.suno-page .price-desc { font-size: 14px; color: var(--el-text-color-secondary); margin-bottom: 24px; margin-top: 8px; }
.suno-page .price-feats { display: flex; flex-direction: column; gap: 10px; margin-bottom: 36px; }
.suno-page .price-feats li { font-size: 14px; color: var(--el-text-color-regular); line-height: 1.4; display: flex; align-items: center; gap: 8px; }
.price-ck { color: #10b981; font-weight: 700; font-size: 14px; flex-shrink: 0; }
.price-btn {
display: block; text-align: center; padding: 14px 0;
border-radius: 9999px; font-size: 15px; font-weight: 600;
transition: background 0.2s, border-color 0.2s, transform 0.15s;
width: 100%; cursor: pointer;
}
.suno-page .price-btn-fill { background: #277186; color: #ffffff !important; border: none; text-decoration: none !important; }
.suno-page .price-btn-fill:hover { background: #1f5a6b; transform: translateY(-1px); text-decoration: none !important; }
.suno-page .price-btn-out { background: var(--el-bg-color); color: var(--el-text-color-primary) !important; border: 1px solid var(--el-border-color-light); text-decoration: none !important; }
.suno-page .price-btn-out:hover { background: var(--el-bg-color-page); text-decoration: none !important; }
@media (max-width: 768px) {
.price-grid { grid-template-columns: 1fr; }
.price-card-feat { transform: none; }
}
.faq-list { display: flex; flex-direction: column; }
.faq-item { border-bottom: 1px solid var(--el-border-color-light); }
.faq-item:first-child { border-top: 1px solid #e5e7eb; }
.faq-q {
display: flex; justify-content: space-between; align-items: center;
padding: 20px 0; cursor: pointer;
font-size: 16px; font-weight: 600; color: var(--el-text-color-primary);
list-style: none; user-select: none;
transition: color 0.2s;
}
.faq-q::-webkit-details-marker { display: none; }
.faq-q:hover { color: var(--el-text-color-primary); }
.faq-chev { font-size: 18px; color: var(--el-text-color-secondary); transition: transform 0.2s; flex-shrink: 0; }
.faq-item[open] .faq-chev { transform: rotate(180deg); }
.faq-a { padding: 0 0 20px; }
.faq-a p { font-size: 15px; color: var(--el-text-color-regular); line-height: 1.7; }
.rel-grid {
display: grid; grid-template-columns: repeat(2, 1fr);
gap: 16px; max-width: 800px; margin: 0 auto;
}
.rel-card {
display: flex; align-items: center; gap: 16px;
padding: 20px 24px; background: var(--el-bg-color);
border: none; border-radius: 20px; box-shadow: 0 2px 12px 0 rgba(0,0,0,0.08);
transition: border-color 0.2s, box-shadow 0.2s;
}
.rel-card:hover { box-shadow: 0 4px 12px rgba(0,0,0,0.05); }
.rel-icon { font-size: 28px; flex-shrink: 0; }
.rel-info { flex: 1; min-width: 0; }
.rel-info h3 { font-size: 15px; font-weight: 700; color: var(--el-text-color-primary); margin-bottom: 2px; }
.rel-info p { font-size: 13px; color: var(--el-text-color-secondary); line-height: 1.4; }
.rel-arrow {
font-size: 18px; color: #cbd5e1; flex-shrink: 0;
transition: color 0.2s, transform 0.2s;
}
.rel-card:hover .rel-arrow { color: var(--el-text-color-regular); transform: translateX(3px); }
@media (max-width: 640px) { .rel-grid { grid-template-columns: 1fr; } } .suno-cta {
padding: 100px 0; background: #0f172a;
text-align: center; position: relative; overflow: hidden;
}
.suno-cta::before {
content: '';
position: absolute; top: -100px; left: 50%;
transform: translateX(-50%);
width: 700px; height: 400px;
background: radial-gradient(ellipse, rgba(39, 113, 134, 0.12) 0%, transparent 70%);
pointer-events: none;
}
.suno-cta h2 {
font-size: clamp(28px, 4vw, 44px);
font-weight: 700; color: #f8fafc;
letter-spacing: normal; margin-bottom: 28px;
position: relative;
}
.suno-cta > div > p {
font-size: clamp(16px, 2vw, 18px);
color: var(--el-text-color-secondary); max-width: 520px;
margin: 0 auto 56px; line-height: 1.6;
position: relative;
}
.cta-actions {
display: flex; gap: 12px; justify-content: center;
flex-wrap: wrap; position: relative;
}
.suno-page .btn-cta-light {
display: inline-flex; align-items: center; gap: 6px;
padding: 14px 32px; background: #277186; color: #ffffff !important;
border-radius: 9999px; font-size: 15px; font-weight: 700;
transition: background 0.2s, transform 0.15s;
text-decoration: none !important;
}
.suno-page .btn-cta-light:hover { background: #1f5a6b; transform: translateY(-1px); text-decoration: none !important; }
.suno-page .btn-cta-ghost {
display: inline-flex; align-items: center;
padding: 14px 32px; background: transparent; color: #94a3b8 !important;
border: 1px solid #334155; border-radius: 9999px;
font-size: 15px; font-weight: 600;
transition: border-color 0.2s, color 0.2s;
text-decoration: none !important;
}
.suno-page .btn-cta-ghost:hover { border-color: var(--el-text-color-regular); color: #e2e8f0 !important; text-decoration: none !important; }
.suno-page code {
background: #dbeafe !important;
padding: 2px 8px !important;
border-radius: 5px !important;
font-size: 13px !important;
font-family: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace !important;
color: #1e40af !important;
border: 1px solid #bfdbfe !important;
}
.s-text-dark { color: var(--el-text-color-primary); }
.s-text-brand { color: #277186; }
.s-section-body { font-size: 16px; color: var(--el-text-color-regular); line-height: 1.8; text-align: center; max-width: 680px; margin: 0 auto; }
.s-section-body p + p { margin-top: 16px; }
.s-text-muted { color: var(--el-text-color-secondary); }
.tag-row {
display: flex; gap: 8px; flex-wrap: wrap;
justify-content: center; margin-top: 16px;
}
.tag-item
```css
{
padding: 4px 12px; background: var(--el-bg-color-page);
border: 1px solid var(--el-border-color-light); border-radius: 9999px;
font-size: 12px; font-weight: 600; color: var(--el-text-color-regular);
}
html.dark .suno-page { background: var(--el-bg-color); color: var(--el-text-color-primary); }
html.dark .suno-page a { color: inherit; }
html.dark .markdown-body .suno-page a { color: inherit !important; }
html.dark .markdown-body .suno-page a.s-btn-primary,
html.dark .markdown-body .suno-page a.price-btn-fill,
html.dark .markdown-body .suno-page a.btn-cta-light { color: #ffffff !important; }
html.dark .markdown-body .suno-page a.s-btn-secondary { color: var(--el-text-color-primary) !important; }
html.dark .markdown-body .suno-page a.price-btn-out { color: var(--el-text-color-primary) !important; }
html.dark .markdown-body .suno-page a.btn-cta-ghost { color: #94a3b8 !important; }
html.dark .markdown-body .suno-page a.btn-cta-ghost:hover { color: var(--el-text-color-primary) !important; }
html.dark .s-bg-white { background: var(--el-bg-color); }
html.dark .s-bg-gray { background: var(--el-bg-color-page); }
html.dark .s-bg-dark { background: var(--el-bg-color); }
html.dark .s-header h2 { color: var(--el-text-color-primary); }
html.dark .s-header p { color: var(--el-text-color-secondary); }
html.dark .suno-page .s-btn-primary { background: #277186; color: #ffffff !important; }
html.dark .suno-page .s-btn-primary:hover { background: #1f5a6b; }
html.dark .suno-page .s-btn-secondary {
background: #1e293b; color: var(--el-text-color-primary) !important;
border-color: #475569;
}
html.dark .suno-page .s-btn-secondary:hover { background: var(--el-border-color); border-color: var(--el-text-color-regular); }
html.dark .suno-hero { background: var(--el-bg-color); }
html.dark .suno-hero::before {
background: radial-gradient(ellipse, rgba(39, 113, 134, 0.15) 0%, transparent 70%);
}
html.dark .hero-badge { background: var(--el-bg-color-page); border-color: var(--el-border-color); color: var(--el-text-color-secondary); }
html.dark .suno-hero h1 { color: var(--el-text-color-primary); }
html.dark .suno-hero h1 span { color: #3b9ab5; }
html.dark .suno-page .hero-subtitle { color: var(--el-text-color-secondary); }
html.dark .hero-highlights .h-item { color: var(--el-text-color-secondary); }
html.dark .hero-highlights .h-div { background: var(--el-border-color); }
html.dark .suno-stats { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .stat-val { color: var(--el-text-color-primary); }
html.dark .stat-lbl { color: var(--el-text-color-regular); }
html.dark .feat-card {
background: var(--el-bg-color-page); border-color: var(--el-border-color);
}
html.dark .feat-card:hover { border-color: var(--el-text-color-regular); box-shadow: 0 4px 16px rgba(0,0,0,0.3); }
html.dark .feat-card h3 { color: var(--el-text-color-primary); }
html.dark .feat-card p { color: var(--el-text-color-secondary); }
html.dark .code-right h2 { color: var(--el-text-color-primary); }
html.dark .code-right > p { color: var(--el-text-color-secondary); }
html.dark .step-num { background: var(--el-border-color); border-color: var(--el-text-color-regular); color: var(--el-text-color-secondary); }
html.dark .step-text h4 { color: var(--el-text-color-primary); }
html.dark .step-text p { color: var(--el-text-color-regular); }
html.dark .suno-page code {
background: #1e3a5f !important; color: #93c5fd !important; border-color: #2563eb !important;
}
html.dark .s-text-dark { color: var(--el-text-color-primary); }
html.dark .s-text-brand { color: #3b9ab5; }
html.dark .s-section-body { color: var(--el-text-color-secondary); }
html.dark .act-card { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .act-card:hover { border-color: var(--el-text-color-regular); box-shadow: 0 4px 16px rgba(0,0,0,0.3); }
html.dark .act-card h3 { color: var(--el-text-color-primary); }
html.dark .act-card p { color: var(--el-text-color-secondary); }
html.dark .uc-card { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .uc-card:hover { border-color: var(--el-text-color-regular); box-shadow: 0 4px 16px rgba(0,0,0,0.3); }
html.dark .uc-card h3 { color: var(--el-text-color-primary); }
html.dark .uc-card p { color: var(--el-text-color-secondary); }
html.dark .stp-num { color: #334155; }
html.dark .stp-card h3 { color: var(--el-text-color-primary); }
html.dark .stp-card p { color: var(--el-text-color-secondary); }
html.dark .stp-conn { background: var(--el-border-color); }
html.dark .cmp-table th { background: var(--el-bg-color-page); color: var(--el-text-color-secondary); }
html.dark .cmp-table td { border-color: var(--el-border-color); }
html.dark .cmp-table th { border-color: var(--el-border-color); }
html.dark .cmp-table td:first-child { color: var(--el-text-color-primary); }
html.dark .cmp-brand { color: var(--el-text-color-primary); }
html.dark .cx { color: var(--el-text-color-regular); }
html.dark .mdl-card { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .mdl-card.mdl-rec { border-color: #277186; }
html.dark .mdl-head h3 { color: var(--el-text-color-primary); }
html.dark .mdl-tag { background: var(--el-border-color); color: var(--el-text-color-secondary); }
html.dark .mdl-tag-blue { background: #1e3a5f; color: #60a5fa; }
html.dark .mdl-tag-purple { background: rgba(39, 113, 134, 0.2); color: #3b9ab5; }
html.dark .mdl-desc { color: var(--el-text-color-secondary); }
html.dark .mdl-feats li { color: var(--el-text-color-secondary); }
html.dark .price-card { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .price-card-feat { border-color: #277186; box-shadow: 0 8px 32px rgba(0,0,0,0.3); }
html.dark .price-tier { color: var(--el-text-color-secondary); }
html.dark .price-amt { color: var(--el-text-color-primary); }
html.dark .price-desc { color: var(--el-text-color-regular); }
html.dark .price-feats li { color: var(--el-text-color-secondary); }
html.dark .suno-page .price-btn-out {
background: #1e293b; color: var(--el-text-color-primary) !important; border-color: #334155;
}
html.dark .suno-page .price-btn-out:hover { background: var(--el-border-color); border-color: var(--el-text-color-regular); }
html.dark .faq-item { border-color: var(--el-border-color); }
html.dark .faq-q { color: var(--el-text-color-primary); }
html.dark .faq-q:hover { color: #ffffff; }
html.dark .faq-chev { color: var(--el-text-color-regular); }
html.dark .faq-a p { color: var(--el-text-color-secondary); }
html.dark .rel-card { background: var(--el-bg-color-page); border-color: var(--el-border-color); }
html.dark .rel-card:hover { border-color: var(--el-text-color-regular); box-shadow: 0 4px 12px rgba(0,0,0,0.3); }
html.dark .rel-info h3 { color: var(--el-text-color-primary); }
html.dark .rel-info p { color: var(--el-text-color-regular); }
html.dark .rel-arrow { color: var(--el-text-color-regular); }
html.dark .rel-card:hover .rel-arrow { color: var(--el-text-color-secondary); }
html.dark .suno-cta { background: #020617; }
html.dark .suno-cta::before {
background: radial-gradient(ellipse, rgba(39, 113, 134, 0.2) 0%, transparent 70%);
}
html.dark .tag-item { background: var(--el-border-color); border-color: var(--el-text-color-regular); color: var(--el-text-color-secondary); }
html.dark .suno-page .btn-cta-light { color: #ffffff !important; }
html.dark .suno-page .btn-cta-ghost { color: #94a3b8 !important; }
html.dark .suno-page .btn-cta-ghost:hover { color: var(--el-text-color-primary) !important; }
html.dark .suno-page .price-btn-fill { color: #ffffff !important; }
</style>
<div class="suno-page">
<section class="suno-hero">
<div class="s-container-narrow">
<div class="hero-badge">
<span class="badge-dot"></span>
Suno API · Ace Data Cloud
</div>
<h1>
Suno API:<br/>
Generate <span>AI Music</span>
</h1>
<p class="hero-subtitle">
Integrate Suno AI music generation capabilities into your application through a stable and comprehensive REST API. Create custom songs, pure music, remixes, covers, and more—all through a unified interface.
```
</p>
<div class="hero-actions">
<a href="https://platform.acedata.cloud/documents/suno-audios" class="s-btn-primary">📄 View Documentation</a>
</div>
<div class="hero-highlights">
<span class="h-item">⚡ 6 Model Versions</span>
<span class="h-div"></span>
<span class="h-item">🎵 16 Actions</span>
<span class="h-div"></span>
<span class="h-item">📄 OpenAPI 3.0 Specification</span>
<span class="h-div"></span>
<span class="h-item">🔑 Bearer Token Authentication</span>
</div>
</div>
</section>
<section class="suno-stats s-section-sm s-bg-gray">
<div class="s-container">
<div class="stats-grid">
<div>
<div class="stat-icon">🎵</div>
<div class="stat-val">16</div>
<div class="stat-lbl">Available Actions</div>
</div>
<div>
<div class="stat-icon">🤖</div>
<div class="stat-val">6</div>
<div class="stat-lbl">Model Versions</div>
</div>
<div>
<div class="stat-icon">📡</div>
<div class="stat-val">12</div>
<div class="stat-lbl">API Endpoints</div>
</div>
<div>
<div class="stat-icon">📦</div>
<div class="stat-val">5</div>
<div class="stat-lbl">Output Formats</div>
</div>
</div>
</div>
</section>
<section class="s-section s-bg-white">
<div class="s-container-narrow">
<div class="s-header">
<h2>Does Suno have an official API?</h2>
</div>
<div class="s-section-body">
<p>Suno currently does not provide a public, self-service REST API. Its music generation features can only be accessed through the Suno official website and application.</p>
<p>Ace Data Cloud fills this gap by providing a <strong class="s-text-dark">stable, production-ready API</strong>, allowing you to programmatically access all of Suno's music generation features—including the latest <strong class="s-text-brand">Chirp v5</strong> model—through a simple REST interface, equipped with OpenAPI specifications, Webhook support, streaming, and pay-as-you-go pricing.</p>
</div>
</div>
</section>
<section class="s-section s-bg-gray">
<div class="s-container">
<div class="s-header">
<h2>All Features of the Suno API</h2>
<p>A comprehensive API suite covering the complete workflow of Suno music generation</p>
</div>
<div class="features-grid">
<div class="feat-card">
<div class="feat-icon">🎵</div>
<h3>Complete Music Generation</h3>
<p>Generate complete songs with lyrics, vocals, and instruments from text prompts, or create pure instrumental music. Supports inspiration mode and custom mode, providing fine control.</p>
</div>
<div class="feat-card">
<div class="feat-icon">🔄</div>
<h3>16 Actions, One API</h3>
<p>Generate, Extend, Cover, Blend, Stems, Remaster, Underpaint, Overpaint, Replace Section, etc.—all accomplished through the <code>/suno/audios</code> endpoint.</p>
</div>
<div class="feat-card">
<div class="feat-icon">🎤</div>
<h3>Custom Persona</h3>
<p>Create and save custom singer voice styles through the Persona API. Reuse a consistent vocal identity across unlimited song generations.</p>
</div>
<div class="feat-card">
<div class="feat-icon">📝</div>
<h3>AI Lyrics Generation</h3>
<p>Automatically generate structured lyrics with paragraph markers (verse, chorus, bridge) using two AI models. Also supports mashup lyrics, blending the lyrics of two songs.</p>
</div>
<div class="feat-card">
<div class="feat-icon">🔀</div>
<h3>Multi-format Output</h3>
<p>Supports output in MP3 (default), MP4 (with visualized video), WAV (lossless audio), and MIDI (music notation) formats. Vocal separation can extract vocals, drums, bass, etc.</p>
</div>
<div class="feat-card">
<div class="feat-icon">⚡</div>
<h3>Streaming and Webhook</h3>
<p>Supports NDJSON real-time streaming for progress updates, or set a <code>callback_url</code> to asynchronously receive results. No polling required.</p>
</div>
</div>
</div>
</section>
<section class="s-section s-bg-white">
<div class="s-container">
<div class="code-split">
<div class="code-left">
<div class="code-wrap">
<div class="code-bar">
<div class="code-dots"><i class="r"></i><i class="y"></i><i class="g"></i></div>
<div class="code-lang">cURL</div>
</div>
<pre class="code-block">curl -X POST https://api.acedata.cloud/suno/audios \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-Type: application/json" \
-d '{
"action": "generate",
"prompt": "A cheerful pop song about a summer road trip",
"model": "chirp-v4",
"custom": false,
"callback_url": "https://your-app.com/webhook"
}'</pre>
</div>
<div style="margin-top: 16px;">
<div class="code-wrap">
<div class="code-bar">
<div class="code-dots"><i class="r"></i><i class="y"></i><i class="g"></i></div>
<div class="code-lang">Response</div>
</div>
<pre class="code-block">{
"success": true,
"task_id": "b3d7a1...",
"data": [{
"id": "a8f2c9...",
"title": "Summer Highway",
"style": "cheerful pop, driving beat",
"duration": 124.5,
"audio_url": "https://cdn1.suno.ai/a8f2c9.mp3",
"image_url": "https://cdn2.suno.ai/a8f2c9.jpeg",
"video_url": "https://cdn1.suno.ai/a8f2c9.mp4",
"state": "succeeded"
}]
}</pre>
</div>
</div>
</div>
<div class="code-right">
<h2>Quick Start - Get Started in 5 Minutes</h2>
<p>A simple REST API using Bearer Token authentication. One request to generate your first AI song.</p>
<div class="explain-steps">
<div class="explain-step">
<div class="step-num">1</div>
<div class="step-text">
<h4>Get API Key</h4>
<p>Register on Ace Data Cloud and obtain your Bearer Token from the console</p>
</div>
</div>
<div class="explain-step">
<div class="step-num">2</div>
<div class="step-text">
<h4>Send POST Request</h4>
<p>Send a request to <code>/suno/audios</code> with your prompt and model preferences</p>
</div>
</div>
<div class="explain-step">
<div class="step-num">3</div>
<div class="step-text">
<h4>Get Your Song</h4>
<p>Receive audio URL, cover image, lyrics, and video—ready to use</p>
</div>
</div>
</div>
</div>
</div>
</div>
</section>
<section class="s-section s-bg-gray">
<div class="s-container">
<div class="s-header">
<h2>16 Actions, One API</h2>
<p>The most comprehensive Suno API—covering every music creation workflow</p>
</div>
<div class="actions-grid">
<div class="act-card">
<div class="act-icon">✨</div>
<h3>Generate</h3>
<p>Create songs from text prompts in inspiration or custom mode</p>
</div>
<div class="act-card">
<div class="act-icon">⏩</div>
<h3>Extend</h3>
<p>Continue a song from any timestamp, adding new lyrics and styles</p>
</div>
<div class="act-card">
<div class="act-icon">🎭</div>
<h3>Cover</h3>
<p>Create a new version of any song in a completely different style</p>
</div>
<div class="act-card">
<div class="act-icon">🔗</div>
<h3>Concat</h3>
<p>Merge continued segments into a seamless complete track</p>
</div>
<div class="act-card">
<div class="act-icon">🎚️</div>
<h3>Stems</h3>
<p>Separate vocals, drums, bass, melodies, and other tracks</p>
</div>
<div class="act-card">
<div class="act-icon">🎧</div>
<h3>Remaster</h3>
<p>Upgrade old songs with improved audio quality (v4.5+ / v5)</p>
</div>
<div class="act-card">
<div class="act-icon">🎸</div>
<h3>Underpaint</h3>
<p>Add instrumental accompaniment to uploaded vocal tracks</p>
</div>
<div class="act-card">
<div class="act-icon">🎤</div>
<h3>Overpaint</h3>
<p>Add AI vocals to uploaded pure instrumental tracks</p>
</div>
<div class="act-card">
<div class="act-icon">✂️</div>
<h3>Replace Section</h3>
<p>Regenerate content in a specified time range of an existing song</p>
</div>
<div class="act-card">
<div class="act-icon">🔀</div>
<h3>Blend</h3>
<p>Fuse two reference songs into a new creation</p>
</div>
<div class="act-card">
<div class="act-icon">📤</div>
<h3>Upload + Extend</h3>
<p>Upload your own audio and continue it with AI generation</p>
</div>
<div class="act-card">
<div class="act-icon">🎯</div>
<h3>Persona</h3>
<p>Maintain a consistent singer identity across multiple songs</p>
</div>
</div>
<div class="tag-row" style="margin-top: 24px;">
<span class="tag-item">+ Upload Cover</span>
<span class="tag-item">+ Persona Voice</span>
<span class="tag-item">+ Sample</span>
<span class="tag-item">+ Full Stems</span>
</div>
</div>
</section>
<section class="s-section s-bg-white">
<div class="s-container">
<div class="s-header">
<h2>What can you build with the Suno API?</h2>
<p>From consumer applications to enterprise platforms—developers are building these projects</p>
</div>
<div class="usecases-grid">
<div class="uc-card">
<div class="uc-icon">🎮</div>
<h3>Music Creation Apps</h3>
<p>Build consumer applications that allow users to generate custom songs, share, and collaborate</p>
</div>
<div class="uc-card">
<div class="uc-icon">🎬</div>
<h3>Video and Content</h3>
<p>Automatically generate copyright-free background music for videos, short films, and podcasts</p>
</div>
<div class="uc-card">
<div class="uc-icon">🤖</div>
<h3>AI Agent and MCP</h3>
<p>Integrate with Claude, ChatGPT, or any AI Agent through our MCP Server for natural language music creation</p>
</div>
<div class="uc-card">
<div class="uc-icon">🏪</div>
<h3>E-commerce and Advertising</h3>
<p>Generate brand music, advertising music, and product audio content in bulk</p>
</div>
</div>
</div>
</section>
<section class="s-section s-bg-gray">
<div class="s-container">
<div class="s-header">
<h2>3 Steps to Get Started Quickly</h2>
<p>From registration to generating your first AI song in under 5 minutes</p>
</div>
<div class="steps-row">
<div class="stp-card">
<div class="stp-num">01</div>
<h3>Register and Get API Key</h3>
<p>Create a free account on Ace Data Cloud. Generate your Bearer Token from the API management console.</p>
</div>
<div class="stp-conn"></div>
<div class="stp-card">
<div class="stp-num">02</div>
<h3>Initiate Your First API Call</h3>
<p>Send a POST request to <code>/suno/audios</code> with a text prompt. You can use SDK, cURL, or any HTTP client.</p>
</div>
<div class="stp-conn"></div>
<div class="stp-card">
<div class="stp-num">03</div>
<h3>Integration and Expansion</h3>
<p>Embed the API into your application. Use Webhook for asynchronous processing and confidently scale to production.</p>
</div>
</div>
<div class="steps-cta">
<a href="https://platform.acedata.cloud/documents/suno-audios" class="s-btn-primary">View Documentation →</a>
</div>
</div>
</section>
<section class="s-section s-bg-white">
<div class="s-container">
<div class="s-header">
<h2>Why choose Ace Data Cloud over other Suno APIs?</h2>
<p>See our comparative advantages on the features that matter most to developers</p>
</div>
<div class="cmp-wrap">
<table class="cmp-table">
<thead>
<tr>
<th>Feature</th>
<th class="cmp-us"><span class="cmp-brand">Ace Data Cloud</span></th>
<th>Other Platforms</th>
</tr>
</thead>
<tbody>
<tr>
<td>Chirp v5 Model</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>16 Actions (Extend, Cover, Stems, etc.)</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>OpenAPI 3.0 Specification</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>Webhook Callback</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>NDJSON Streaming</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>Custom Persona</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>MP3 + MP4 + WAV + MIDI</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>MCP Server (AI Agent Integration)</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>Pay-as-you-go</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
<tr>
<td>No Watermark</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td>Partially supported</td>
</tr>
</tbody>
</table>
</div>
</div>
</section>
<section class="s-section s-bg-gray">
<div class="s-container">
<div class="s-header">
<h2>Comparison of Suno with Other AI Models</h2>
<p>Hesitating between Suno, Udio, and other AI music platforms? Check out their comparison.</p>
</div>
<div class="cmp-wrap">
<table class="cmp-table">
<thead>
<tr>
<th>Capability</th>
<th class="cmp-us"><span class="cmp-brand">Suno (via Ace Data)</span></th>
<th>Udio</th>
<th>Others</th>
</tr>
</thead>
<tbody>
<tr>
<td>Songs with Vocals</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
</tr>
<tr>
<td>Custom Lyrics</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
</tr>
<tr>
<td>Pure Instrumental</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="ck">✓</span></td>
<td><span class="ck">✓</span></td>
</tr>
<tr>
<td>Song Continuation and Remixing</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
</tr>
<tr>
<td>Vocal Separation</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
<td><span class="cx">✗</span></td>
</tr>
<tr>
<td>Persona Voice Cloning</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
<td><span class="cx">✗</span></td>
</tr>
<tr>
<td>API Access</td>
<td class="cmp-us"><span class="ck">✓</span></td>
<td><span class="cx">✗</span></td>
<td>Limited</td>
</tr>
</tbody>
</table>
</div>
</div>
</section>
<section class="s-section s-bg-white">
<div class="s-container">
<div class="s-header">
<h2>Which model is right for you?</h2>
<p>Choose from 6 Suno model versions based on your quality and speed needs</p>

## Quick Start

- Base URL: [https://api.acedata.cloud](https://api.acedata.cloud)
- Service page: [Suno Music Generation on Ace Data Cloud](https://platform.acedata.cloud/service/suno)
- Docs: [Developer documentation](https://docs.acedata.cloud)

```bash
curl --request POST "https://api.acedata.cloud/suno/audios" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{}'
```

## APIs and Guides

Explore the supported endpoints and integration guides for Suno Music Generation.

| API | Path | Integration Guidance |
| ---- | ---- | ------------ |
| [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) | `/suno/audios` | [Suno Audios Generation API Integration Guide](https://platform.acedata.cloud/documents/d016ee3f-421b-4b6e-989a-8beba8701701) |
| [Suno Persona API](https://platform.acedata.cloud/documents/78bb6c62-6ce0-490f-a7df-e89d80ec0583) | `/suno/persona` | [Suno Persona API Integration Guide](https://platform.acedata.cloud/documents/a1ae233c-c52a-4a62-97dd-0db0c089da5a) |
| [Suno MP4 API](https://platform.acedata.cloud/documents/adf030f2-ac31-4342-bb65-afd9669272f9) | `/suno/mp4` | [Suno MP4 API Integration Guide](https://platform.acedata.cloud/documents/9dff19bb-3360-4578-8115-91c5efc130a3) |
| [Suno Vox API](https://platform.acedata.cloud/documents/ae804856-897a-4f5b-9329-8514a86a1d43) | `/suno/vox` | [Suno Vox API Integration Guide](https://platform.acedata.cloud/documents/4d487ecc-0b64-4e8f-a40b-908b9d776c76) |
| [$t(document_title_suno_timing_generation_api)](https://platform.acedata.cloud/documents/e8b5a84f-742f-4078-8b7d-a52a68aa253f) | `/suno/timing` | [Suno Timing API Integration Guide](https://platform.acedata.cloud/documents/149a2dd6-8af9-43f1-8994-0f4466b16c6f) |
| [Suno Wav API](https://platform.acedata.cloud/documents/c55b2b82-416b-46d7-9854-4c3bf28a3cc5) | `/suno/wav` | [Suno Wav API Integration Guide](https://platform.acedata.cloud/documents/e48efa85-ed94-4ea8-8613-c16d734a3138) |
| [Suno MIDI API](https://platform.acedata.cloud/documents/dc315c81-ebfa-4c5a-b6e8-af593dd67d86) | `/suno/midi` | [Suno MIDI API Integration Guide](https://platform.acedata.cloud/documents/d0557c7c-b518-4c42-b482-cc84d62b208b) |
| [Suno Style Generation API](https://platform.acedata.cloud/documents/864d5f20-2e97-4334-b0bf-f80a60f0810c) | `/suno/style` | [Suno Style API Integration Guide](https://platform.acedata.cloud/documents/2835d3d3-fcfa-4e31-a4be-33a93b84a450) |
| [Suno Lyrics Generation API](https://platform.acedata.cloud/documents/514d82dc-f7ab-4638-9f21-8b9275916b08) | `/suno/lyrics` | [Suno Lyrics Generation API Integration Guide](https://platform.acedata.cloud/documents/f1c66741-a488-43ca-91fc-e53fbbda639a) |
| [Suno MashupLyrics Generation API](https://platform.acedata.cloud/documents/851f9405-5f19-405a-8dbd-df4bd88e05a2) | `/suno/mashup-lyrics` | [Suno Mashup Lyrics Generation API Integration Guide](https://platform.acedata.cloud/documents/ec26e17f-7709-40f4-ad87-2f50c16f94b0) |
| [Suno Tasks API](https://platform.acedata.cloud/documents/b0dd9823-0e01-4c75-af83-5a6e2e05bfed) | `/suno/tasks` | [Suno Tasks API Integration Guide](https://platform.acedata.cloud/documents/d3868342-7f11-4670-bd31-61a63663cb10) |
| [Suno Upload API](https://platform.acedata.cloud/documents/766db278-012c-43c4-9245-5f18d8dc4d82) | `/suno/upload` | [Suno Upload API Integration Guide](https://platform.acedata.cloud/documents/26092dda-23d9-4874-9916-e12db6fce3b5) |

## Related Resources

- [Ace Data Cloud Developer Platform](https://platform.acedata.cloud)
- [Ace Data Cloud Docs](https://docs.acedata.cloud)
- [Status Page](https://status.acedata.cloud)
- [Ace Data Cloud GitHub Organization](https://github.com/AceDataCloud)

## Support

If you meet any issue, please check [support info](https://platform.acedata.cloud/support) or browse the latest documentation on [docs.acedata.cloud](https://docs.acedata.cloud).