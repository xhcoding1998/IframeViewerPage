<script setup lang="ts">
const steps = [
  {
    num: '01',
    title: '下载压缩包',
    desc: '点击「免费下载」按钮，将 IframeViewer.zip 保存到本地固定位置（如桌面）。',
  },
  {
    num: '02',
    title: '解压文件',
    desc: '右键 zip → 解压到当前文件夹，得到含 manifest.json 的扩展目录。解压后请勿移动该目录。',
  },
  {
    num: '03',
    title: '打开扩展页',
    desc: '地址栏输入 chrome://extensions/ 回车，或通过菜单 → 更多工具 → 扩展程序 进入。',
    mono: 'chrome://extensions/',
  },
  {
    num: '04',
    title: '开启开发者模式',
    desc: '点击页面右上角「开发者模式」开关，变蓝即代表已启用。',
  },
  {
    num: '05',
    title: '加载扩展',
    desc: '点击「加载已解压的扩展程序」，选择第 2 步解压出的文件夹（含 manifest.json），确认即完成。',
  },
  {
    num: '06',
    title: '开始使用',
    desc: '打开任意含 iframe 的页面，点击工具栏扩展图标，点击「扫描 iframe」按钮即可。',
  },
]

const usageFlow = [
  { icon: '🌐', text: '打开含 iframe 的页面' },
  { icon: '🖱️', text: '点击扩展图标' },
  { icon: '🔍', text: '扫描 iframe' },
  { icon: '📸', text: '截取快照' },
  { icon: '🔗', text: '查看 URL 参数' },
  { icon: '💾', text: '下载 PNG' },
]
</script>

<template>
  <section class="install" id="install">
    <div class="container">

      <div class="section-header">
        <div class="section-num">§ 02</div>
        <div class="section-right">
          <h2 class="section-title">安装指南</h2>
          <p class="section-desc">
            无需 Chrome 应用商店，<br />
            6 步、60 秒内完成安装。
          </p>
        </div>
      </div>

      <div class="rule" />

      <div class="steps-grid">
        <!-- 步骤列表 -->
        <div class="steps-list">
          <div v-for="step in steps" :key="step.num" class="step">
            <div class="step-num">{{ step.num }}</div>
            <div class="step-body">
              <h3 class="step-title">{{ step.title }}</h3>
              <p class="step-desc">{{ step.desc }}</p>
              <code v-if="step.mono" class="step-mono">{{ step.mono }}</code>
            </div>
          </div>
        </div>

        <!-- 右侧补充信息 -->
        <div class="steps-aside">
          <!-- 使用流程 -->
          <div class="aside-card">
            <div class="aside-label">使用流程</div>
            <div class="flow-list">
              <div v-for="(item, i) in usageFlow" :key="i" class="flow-item">
                <span class="flow-icon">{{ item.icon }}</span>
                <span class="flow-text">{{ item.text }}</span>
                <span v-if="i < usageFlow.length - 1" class="flow-arrow">↓</span>
              </div>
            </div>
          </div>

          <!-- 安全提示 -->
          <div class="aside-note">
            <div class="note-icon">⚠</div>
            <div>
              <p class="note-title">关于安全提示</p>
              <p class="note-desc">
                Chrome 可能提示「此扩展未在应用商店中」，点击「保留」即可正常使用。
                扩展代码完全透明，欢迎审阅源码。
              </p>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.install {
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
  margin-bottom: 56px;
}

.steps-grid {
  display: grid;
  grid-template-columns: 1fr 340px;
  gap: 64px;
  align-items: start;
}

/* ─── 步骤列表 ─── */
.steps-list {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.step {
  display: flex;
  gap: 28px;
  padding: 28px 0;
  border-bottom: 1px solid var(--border);
  transition: background 0.15s;
}

.step:first-child {
  padding-top: 0;
}

.step:last-child {
  border-bottom: none;
}

.step-num {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 900;
  color: var(--accent);
  line-height: 1;
  flex-shrink: 0;
  width: 48px;
  padding-top: 2px;
}

.step-body {
  flex: 1;
}

.step-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 8px;
  color: var(--text);
}

.step-desc {
  font-size: 0.9rem;
  color: var(--text-muted);
  line-height: 1.75;
  font-weight: 300;
}

.step-mono {
  display: inline-block;
  margin-top: 10px;
  font-size: 11px;
  color: var(--accent);
  background: var(--accent-bg);
  border: 1px solid rgba(29, 78, 216, 0.15);
  padding: 4px 10px;
  border-radius: 3px;
}

/* ─── 右侧 ─── */
.steps-aside {
  display: flex;
  flex-direction: column;
  gap: 20px;
  position: sticky;
  top: 80px;
}

.aside-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 24px;
}

.aside-label {
  font-family: var(--font-mono);
  font-size: 10px;
  color: var(--text-light);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.flow-list {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.flow-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 0;
  position: relative;
}

.flow-icon {
  font-size: 1.2rem;
  width: 32px;
  text-align: center;
  flex-shrink: 0;
}

.flow-text {
  font-size: 13px;
  color: var(--text);
  flex: 1;
  font-weight: 500;
}

.flow-arrow {
  font-size: 11px;
  color: var(--text-light);
  position: absolute;
  left: 14px;
  bottom: -4px;
}

.aside-note {
  display: flex;
  gap: 14px;
  background: #FFFBF5;
  border: 1px solid #E8D5BB;
  border-radius: 6px;
  padding: 18px 20px;
}

.note-icon {
  font-size: 1rem;
  color: #B45309;
  flex-shrink: 0;
  padding-top: 1px;
}

.note-title {
  font-size: 13px;
  font-weight: 600;
  color: #B45309;
  margin-bottom: 6px;
}

.note-desc {
  font-size: 12px;
  color: var(--text-muted);
  line-height: 1.7;
  font-weight: 300;
}

@media (max-width: 900px) {
  .install {
    padding: 80px 24px;
  }

  .steps-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .section-header {
    flex-direction: column;
    gap: 16px;
  }

  .steps-aside {
    position: static;
  }
}
</style>
