
# MiMo TTS 极简语音合成工具

> 目前tts模型限时免费中

一个基于 Web 的极简语音合成界面，用于与小米 MiMo TTS API 交互。

## 功能特点

- 🎙️ **语音合成**：将文本转换为自然语音
- 🎵 **唱歌模式**：支持歌词演唱
- 🎨 **风格标签**：多种预设风格（开心、悲伤、温柔、方言、角色扮演等）
- 💭 **声音事件**：插入咳嗽、停顿、叹气等音效
- ⚡ **快速模板**：内置常用场景模板
- 🔧 **自定义风格**：支持自定义风格描述
- 📥 **下载导出**：支持下载音频和复制 Base64 数据
- 💾 **本地存储**：可选保存 API Key 到本地

## 快速开始

### 1. 获取 API Key

前往 [小米 MiMo 开发者平台](https://api.xiaomimimo.com) 注册并获取 API Key。

### 2. 打开工具

直接在浏览器中打开 `index.html` 文件，无需安装任何依赖。

### 3. 配置与使用

1. 在 **API 配置** 区域输入你的 API Key
2. 勾选 **保存到本地**（可选）
3. 在 **合成配置** 区域：
   - 选择风格标签（点击切换）
   - 输入自定义风格（可选）
   - 插入声音事件（可选）
   - 输入要合成的文本
4. 点击 **生成语音** 按钮
5. 在 **生成结果** 区域播放、下载或复制音频

## 技术栈

- **前端**：纯 HTML5 + CSS3 + JavaScript
- **API**：小米 MiMo TTS API v1
- **特性**：响应式设计、无依赖、开箱即用

## 浏览器兼容性

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## 项目结构

```

mimo-tts-tool/
├── index.html      # 主界面文件（包含所有代码）
└── README.md       # 本文件

```

> **注意**：这是一个单文件应用，所有 HTML、CSS 和 JavaScript 都包含在 `index.html` 中，便于部署和分享。

## API 参考

### 请求地址
```

POST https://api.xiaomimimo.com/v1/chat/completions

```

### 请求头
| 参数 | 值 |
|------|-----|
| Content-Type | application/json |
| api-key | 你的 API Key |

### 请求体示例
```json
{
  "model": "mimo-v2-tts",
  "messages": [
    {
      "role": "assistant",
      "content": "<style>唱歌</style>小星星，亮晶晶"
    }
  ],
  "audio": {
    "format": "wav",
    "voice": "mimo_default"
  }
}
```

响应示例

```json
{
  "choices": [
    {
      "message": {
        "audio": {
          "data": "base64encodedaudio...",
          "format": "wav",
          "voice": "mimo_default"
        }
      }
    }
  ]
}
```

风格标签说明

标签	说明	
🎵 唱歌	演唱模式，适合歌词	
开心	愉快、积极的语气	
悲伤	低沉、伤感的语气	
温柔	柔和、亲切的语气	
兴奋	激动、 energetic 的语气	
慵懒	放松、缓慢的语速	
东北话	东北方言特色	
四川话	四川方言特色	
粤语	广东话特色	
台湾腔	台湾口音特色	
孙悟空	模仿孙悟空语气	
林黛玉	模仿林黛玉语气	
撒娇	撒娇语气	
深情	深情款款	

声音事件标记

在文本中插入以下标记，可添加对应音效：

- `[咳嗽]` - 咳嗽声
- `[停顿]` - 短暂停顿
- `[叹气]` - 叹气声
- `[笑声]` - 笑声
- `[哭泣]` - 哭泣声

自定义开发

添加新的风格标签

在 `index.html` 的 `#styleTags` 容器中添加：

```html
<span class="tag" data-style="新风格">新风格</span>
```

添加新的声音事件

在 `.events-container` 中添加按钮：

```html
<button class="event-btn" onclick="insertEvent('[新事件]')">新事件</button>
```

添加新的快速模板

在 `loadTemplate` 函数中添加：

```javascript
newtemplate: {
    user: '用户提示',
    assistant: '合成文本内容'
}
```

注意事项

1. API Key 安全：建议仅在本地环境保存 API Key，公共环境请手动输入
2. 网络要求：需要能够访问 `api.xiaomimimo.com`
3. 文本长度：单次合成文本建议不超过 500 字
4. 使用限制：请遵守小米 MiMo API 的使用条款和限制

更新日志

v1.0.0 (2026-03-24)
- ✨ 初始版本发布
- 🎵 支持唱歌模式
- 🎨 14 种预设风格标签
- 💭 5 种声音事件
- ⚡ 6 个快速模板
- 📱 响应式设计
- 💾 本地存储 API Key

