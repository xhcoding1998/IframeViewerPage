<script setup lang="ts">
const DOWNLOAD_URL = '/IframeViewer.zip'

function handleDownload() {
  const a = document.createElement('a')
  a.href = DOWNLOAD_URL
  a.download = 'IframeViewer.zip'
  a.click()
}
</script>

<template>
  <div>
    <!-- 顶部导航栏 -->
    <header class="nav">
      <div class="nav-inner">
        <div class="nav-brand">
          <span class="brand-mark">◆</span>
          <span class="brand-name">Iframe 检测器</span>
        </div>
        <nav class="nav-links">
          <a href="#features">功能</a>
          <a href="#install">安装</a>
          <button class="nav-download" @click="handleDownload">下载</button>
        </nav>
      </div>
    </header>

    <!-- 英雄区 -->
    <section class="hero">
      <div class="hero-inner">

        <!-- 左侧主内容 -->
        <div class="hero-content">
          <div class="hero-eyebrow">
            <code>Chrome Extension · MV3</code>
            <span class="divider">—</span>
            <span>前端开发工具</span>
          </div>

          <h1 class="hero-title">
            扫描、解析<br />
            <em>截图每一个</em><br />
            iframe
          </h1>

          <p class="hero-desc">
            一键检测页面所有 <code>&lt;iframe&gt;</code>，自动拆解
            src URL 参数，精准裁剪截图快照——无论同域还是跨域。
          </p>

          <div class="hero-actions">
            <button class="btn-primary" @click="handleDownload">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
                <polyline points="7 10 12 15 17 10" />
                <line x1="12" y1="15" x2="12" y2="3" />
              </svg>
              免费下载
            </button>
            <a class="btn-text" href="#install">查看安装教程 →</a>
          </div>

          <div class="hero-stats">
            <div class="stat">
              <span class="stat-val">MV3</span>
              <span class="stat-label">Manifest 版本</span>
            </div>
            <div class="stat-sep" />
            <div class="stat">
              <span class="stat-val">&lt; 500<span class="stat-unit">KB</span></span>
              <span class="stat-label">压缩包大小</span>
            </div>
            <div class="stat-sep" />
            <div class="stat">
              <span class="stat-val">0</span>
              <span class="stat-label">数据收集</span>
            </div>
          </div>
        </div>

        <!-- 右侧演示面板 -->
        <div class="hero-demo">
          <div class="demo-label">扫描结果预览</div>
          <div class="demo-panel">
            <div class="demo-toolbar">
              <div class="demo-title-row">
                <span class="demo-ext-name">Iframe 检测器</span>
                <span class="demo-count">发现 3 个</span>
              </div>
              <button class="demo-scan-btn">扫描 iframe</button>
            </div>

            <div class="demo-list">
              <div class="demo-item" v-for="item in demoItems" :key="item.src">
                <div class="demo-thumb" :style="{ background: item.color }" />
                <div class="demo-info">
                  <code class="demo-src">{{ item.src }}</code>
                  <div class="demo-meta">{{ item.size }} · {{ item.domain }}</div>
                </div>
                <div class="demo-btns">
                  <button class="demo-btn">截图</button>
                  <button class="demo-btn demo-btn-outline">参数</button>
                </div>
              </div>
            </div>

            <!-- URL 参数展开 -->
            <div class="demo-params">
              <div class="demo-params-title">URL 参数解析</div>
              <div class="param-row" v-for="p in demoParams" :key="p.key">
                <code class="param-key">{{ p.key }}</code>
                <code class="param-val">{{ p.val }}</code>
                <button class="param-copy">复制</button>
              </div>
            </div>
          </div>
        </div>

      </div>
    </section>
  </div>
</template>

<script lang="ts">
const demoItems = [
  { src: 'example.com/embed?id=123&lang=zh', size: '640×360', domain: 'example.com', color: 'linear-gradient(135deg, #1D4ED8 0%, #3B82F6 100%)' },
  { src: 'player.site/video?v=abc&autoplay=1', size: '1280×720', domain: 'player.site', color: 'linear-gradient(135deg, #1E40AF 0%, #60A5FA 100%)' },
  { src: 'srcdoc (内联 HTML)', size: '300×200', domain: '—', color: 'linear-gradient(135deg, #1D4ED8 0%, #93C5FD 100%)' },
]

const demoParams = [
  { key: 'id', val: '123' },
  { key: 'lang', val: 'zh' },
  { key: 'autoplay', val: '1' },
]
</script>

<style scoped>
/* ─── 导航 ─── */
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: rgba(249, 247, 244, 0.9);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
}

.nav-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 48px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-brand {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 600;
  font-size: 15px;
}

.brand-mark {
  color: var(--accent);
  font-size: 10px;
}

.brand-name {
  font-family: var(--font-mono);
  font-size: 13px;
  letter-spacing: 0.02em;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 32px;
  font-size: 14px;
  color: var(--text-muted);
}

.nav-links a {
  transition: color 0.15s;
}

.nav-links a:hover {
  color: var(--text);
}

.nav-download {
  background: var(--text);
  color: var(--bg);
  border: none;
  padding: 8px 20px;
  border-radius: var(--radius);
  font-family: var(--font-body);
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  letter-spacing: 0.02em;
}

.nav-download:hover {
  background: var(--accent);
}

/* ─── 英雄区 ─── */
.hero {
  padding: 140px 48px 100px;
  max-width: 1200px;
  margin: 0 auto;
}

.hero-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

.hero-eyebrow {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 12px;
  color: var(--text-muted);
  margin-bottom: 28px;
  font-family: var(--font-mono);
  letter-spacing: 0.04em;
}

.hero-eyebrow code {
  color: var(--accent);
}

.divider {
  color: var(--border-strong);
}

.hero-title {
  font-family: var(--font-display);
  font-size: clamp(3rem, 5vw, 4.2rem);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 28px;
  color: var(--text);
}

.hero-title em {
  font-style: italic;
  color: var(--accent);
}

.hero-desc {
  font-size: 1rem;
  color: var(--text-muted);
  line-height: 1.8;
  margin-bottom: 40px;
  font-weight: 300;
  max-width: 420px;
}

.hero-desc code {
  font-size: 0.85em;
  background: var(--bg-alt);
  border: 1px solid var(--border);
  padding: 1px 6px;
  border-radius: 3px;
  color: var(--text);
}

.hero-actions {
  display: flex;
  align-items: center;
  gap: 28px;
  margin-bottom: 48px;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--accent);
  color: #fff;
  border: none;
  padding: 14px 28px;
  border-radius: var(--radius);
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.15s;
  letter-spacing: 0.02em;
}

.btn-primary:hover {
  background: #1E40AF;
  transform: translateY(-1px);
}

.btn-text {
  font-size: 14px;
  color: var(--text-muted);
  transition: color 0.15s;
  font-weight: 500;
  border-bottom: 1px solid transparent;
  padding-bottom: 1px;
}

.btn-text:hover {
  color: var(--text);
  border-color: var(--border-strong);
}

.hero-stats {
  display: flex;
  align-items: center;
  gap: 0;
  padding: 20px 0;
  border-top: 1px solid var(--border);
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding-right: 32px;
}

.stat-val {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 700;
  color: var(--text);
  line-height: 1;
}

.stat-unit {
  font-size: 0.9rem;
  font-weight: 400;
}

.stat-label {
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  font-family: var(--font-mono);
}

.stat-sep {
  width: 1px;
  height: 36px;
  background: var(--border);
  margin-right: 32px;
  flex-shrink: 0;
}

/* ─── 演示面板 ─── */
.hero-demo {
  position: relative;
}

.demo-label {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 12px;
}

.demo-panel {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06), 0 20px 60px rgba(0,0,0,0.07);
}

.demo-toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 18px;
  border-bottom: 1px solid var(--border);
  background: var(--bg-alt);
}

.demo-title-row {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.demo-ext-name {
  font-size: 13px;
  font-weight: 600;
  color: var(--text);
}

.demo-count {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--accent);
}

.demo-scan-btn {
  background: var(--accent);
  color: white;
  border: none;
  padding: 6px 14px;
  border-radius: 3px;
  font-family: var(--font-mono);
  font-size: 11px;
  cursor: pointer;
  font-weight: 500;
}

.demo-list {
  padding: 12px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  border-bottom: 1px solid var(--border);
}

.demo-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 12px;
  border: 1px solid var(--border);
  border-radius: 4px;
  background: var(--bg);
  transition: border-color 0.15s;
}

.demo-item:hover {
  border-color: var(--border-strong);
}

.demo-thumb {
  width: 36px;
  height: 28px;
  border-radius: 3px;
  flex-shrink: 0;
}

.demo-info {
  flex: 1;
  min-width: 0;
}

.demo-src {
  display: block;
  font-size: 11px;
  color: var(--text);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-bottom: 3px;
}

.demo-meta {
  font-size: 10px;
  color: var(--text-light);
  font-family: var(--font-mono);
}

.demo-btns {
  display: flex;
  gap: 5px;
  flex-shrink: 0;
}

.demo-btn {
  font-size: 10px;
  font-family: var(--font-mono);
  padding: 4px 9px;
  border-radius: 3px;
  border: none;
  background: var(--accent);
  color: white;
  cursor: pointer;
  font-weight: 500;
}

.demo-btn-outline {
  background: transparent;
  color: var(--text-muted);
  border: 1px solid var(--border-strong);
}

/* URL 参数区 */
.demo-params {
  padding: 14px 16px;
}

.demo-params-title {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-light);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin-bottom: 10px;
}

.param-row {
  display: flex;
  align-items: center;
  gap: 0;
  padding: 6px 0;
  border-bottom: 1px solid var(--border);
}

.param-row:last-child {
  border-bottom: none;
}

.param-key {
  width: 80px;
  font-size: 11px;
  color: var(--accent);
  flex-shrink: 0;
}

.param-val {
  flex: 1;
  font-size: 11px;
  color: var(--text);
}

.param-copy {
  font-size: 10px;
  color: var(--text-light);
  background: none;
  border: 1px solid var(--border);
  padding: 2px 8px;
  border-radius: 3px;
  cursor: pointer;
  font-family: var(--font-mono);
  transition: color 0.15s, border-color 0.15s;
}

.param-copy:hover {
  color: var(--accent);
  border-color: var(--accent);
}

/* ─── 响应式 ─── */
@media (max-width: 900px) {
  .hero {
    padding: 120px 24px 80px;
  }

  .hero-inner {
    grid-template-columns: 1fr;
    gap: 60px;
  }

  .nav-inner {
    padding: 0 24px;
  }
}
</style>
