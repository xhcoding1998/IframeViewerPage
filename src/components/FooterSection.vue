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
  <!-- CTA 区域 -->
  <section class="cta">
    <div class="cta-inner">
      <div class="cta-left">
        <p class="cta-label">准备好了吗？</p>
        <h2 class="cta-title">
          立即下载，<br />
          <em>开始调试</em>
        </h2>
      </div>
      <div class="cta-right">
        <button class="btn-primary" @click="handleDownload">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
            <polyline points="7 10 12 15 17 10" />
            <line x1="12" y1="15" x2="12" y2="3" />
          </svg>
          免费下载 Iframe 检测器
        </button>
        <p class="cta-sub">Chrome & Edge · Manifest V3 · 完全免费</p>
      </div>
    </div>
  </section>

  <!-- 页脚 -->
  <footer class="footer">
    <div class="footer-inner">
      <div class="footer-brand">
        <span class="brand-mark">◆</span>
        <span class="brand-name">Iframe 检测器</span>
      </div>
      <p class="footer-copy">
        © {{ new Date().getFullYear() }} · 完全免费 · 不收集数据 · 代码透明可审阅
      </p>
    </div>
  </footer>
</template>

<style scoped>
/* ─── CTA ─── */
.cta {
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  background: var(--bg-alt);
}

.cta-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 80px 48px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 60px;
}

.cta-label {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.cta-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -0.02em;
  color: var(--text);
}

.cta-title em {
  font-style: italic;
  color: var(--accent);
}

.cta-right {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 14px;
  flex-shrink: 0;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--accent);
  color: white;
  border: none;
  padding: 16px 32px;
  border-radius: var(--radius);
  font-family: var(--font-body);
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.15s;
  letter-spacing: 0.01em;
  white-space: nowrap;
}

.btn-primary:hover {
  background: #1E40AF;
  transform: translateY(-1px);
}

.cta-sub {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.04em;
}

/* ─── 页脚 ─── */
.footer {
  background: var(--bg);
  padding: 32px 48px;
}

.footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 8px;
}

.brand-mark {
  color: var(--accent);
  font-size: 9px;
}

.brand-name {
  font-family: var(--font-mono);
  font-size: 12px;
  color: var(--text-muted);
}

.footer-copy {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.04em;
}

@media (max-width: 900px) {
  .cta-inner {
    flex-direction: column;
    align-items: flex-start;
    padding: 60px 24px;
    gap: 40px;
  }

  .cta-right {
    align-items: flex-start;
    width: 100%;
  }

  .footer {
    padding: 24px;
  }

  .footer-inner {
    flex-direction: column;
    gap: 12px;
    text-align: center;
  }
}
</style>
