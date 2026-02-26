<script setup lang="ts">
const features = [
  {
    num: '01',
    title: '扫描全部 iframe',
    desc: '一键检测页面所有 iframe 元素，展示 src、尺寸、id、name、title、协议、域名等完整属性。',
    tag: 'content.js',
  },
  {
    num: '02',
    title: 'URL 参数解析',
    desc: 'src 自动拆分为 Base URL + 参数表格，每项一键复制。嵌入链接调试从未如此轻松。',
    tag: 'popup.js',
  },
  {
    num: '03',
    title: '精准截图裁剪',
    desc: '自动滚动 iframe 到视口中央，captureVisibleTab 截图后按坐标精确裁剪，所见即所得。',
    tag: 'background.js',
  },
  {
    num: '04',
    title: '跨域也能截图',
    desc: '截取浏览器渲染快照，不依赖 DOM 访问权限。无论同域还是跨域 iframe 均可正常截图。',
    tag: 'captureVisibleTab',
  },
  {
    num: '05',
    title: '下载 PNG',
    desc: '截图后直接下载为 PNG 文件。存档、汇报、提 Bug 时附图，无需额外截图工具介入。',
    tag: 'popup.js',
  },
  {
    num: '06',
    title: 'srcdoc 兼容',
    desc: '内联 HTML 的 srcdoc iframe 无法解析 URL 参数，但仍可完整截图预览渲染结果。',
    tag: 'content.js',
  },
]
</script>

<template>
  <section class="features" id="features">
    <div class="container">

      <div class="section-header">
        <div class="section-num">§ 01</div>
        <div class="section-right">
          <h2 class="section-title">核心功能</h2>
          <p class="section-desc">
            6 个功能覆盖 iframe 调试全流程——<br />
            扫描、解析、截图、下载，一个扩展搞定。
          </p>
        </div>
      </div>

      <div class="rule" />

      <div class="grid">
        <div v-for="feat in features" :key="feat.num" class="card">
          <div class="card-top">
            <span class="card-num">{{ feat.num }}</span>
            <code class="card-tag">{{ feat.tag }}</code>
          </div>
          <h3 class="card-title">{{ feat.title }}</h3>
          <p class="card-desc">{{ feat.desc }}</p>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.features {
  padding: 100px 48px;
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  display: flex;
  gap: 60px;
  align-items: flex-start;
  margin-bottom: 40px;
}

.section-num {
  font-family: var(--font-display);
  font-size: clamp(3.5rem, 6vw, 6rem);
  font-weight: 900;
  color: var(--bg-alt);
  line-height: 1;
  flex-shrink: 0;
  /* 文字描边 */
  -webkit-text-stroke: 1.5px var(--border-strong);
  user-select: none;
}

.section-right {
  padding-top: 8px;
}

.section-title {
  font-family: var(--font-display);
  font-size: clamp(1.8rem, 3vw, 2.6rem);
  font-weight: 700;
  letter-spacing: -0.02em;
  margin-bottom: 12px;
  color: var(--text);
}

.section-desc {
  font-size: 0.95rem;
  color: var(--text-muted);
  line-height: 1.8;
  font-weight: 300;
}

.rule {
  height: 1px;
  background: var(--border);
  margin-bottom: 48px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0;
  border: 1px solid var(--border);
  border-radius: 4px;
  overflow: hidden;
}

.card {
  padding: 32px 28px;
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  transition: background 0.15s;
}

.card:hover {
  background: var(--accent-bg);
}

/* 每行最后一个去掉右边框 */
.card:nth-child(3n) {
  border-right: none;
}

/* 最后一行去掉底边框 */
.card:nth-last-child(-n+3) {
  border-bottom: none;
}

.card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.card-num {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--text-light);
  letter-spacing: 0.08em;
}

.card-tag {
  font-size: 10px;
  color: var(--accent);
  background: var(--accent-bg);
  border: 1px solid rgba(29, 78, 216, 0.15);
  padding: 2px 8px;
  border-radius: 3px;
}

.card-title {
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 10px;
  color: var(--text);
  letter-spacing: -0.01em;
}

.card-desc {
  font-size: 0.88rem;
  color: var(--text-muted);
  line-height: 1.75;
  font-weight: 300;
}

@media (max-width: 900px) {
  .features {
    padding: 80px 24px;
  }

  .grid {
    grid-template-columns: 1fr 1fr;
  }

  .card:nth-child(3n) {
    border-right: 1px solid var(--border);
  }

  .card:nth-child(2n) {
    border-right: none;
  }

  .card:nth-last-child(-n+2) {
    border-bottom: none;
  }

  .card:nth-last-child(-n+3) {
    border-bottom: 1px solid var(--border);
  }

  .section-header {
    flex-direction: column;
    gap: 16px;
  }
}

@media (max-width: 600px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .card:nth-child(n) {
    border-right: none;
  }

  .card:last-child {
    border-bottom: none;
  }
}
</style>
