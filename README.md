YOLO+DeepSeek农作物病虫害检测系统
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/82ce49cc87d0403a92bc5ded5318ab38.png)


**【结合Deepseek，Qwen】**
**【可以上传文件夹批量检测，可以导出图片检测结果为PDF文件】**

可以实现检测图片、批量检测图片、视频检测、摄像头检测四种方式。

能够检测出[“苹果-黑腐病”, “苹果-健康”, “苹果-结痂”, “甜椒-细菌性斑疹”, “甜椒-健康”, “木薯-褐条病”, “木薯-细菌性枯萎病”, “木薯-绿斑病”, “樱桃-健康”, “樱桃-白粉病”, “玉米-叶斑病”, “玉米-普通锈病”, “玉米-健康”, “葡萄-黑腐病”, “葡萄-健康”, “葡萄-叶枯病”, “木薯-健康”, “木薯-花叶病毒”, “玉米-大斑病”, “柑桔-黄龙病”, “桃子-桃细菌性穿孔病”, “桃子-健康”, “土豆-早疫病”, “土豆-健康”, “土豆-晚疫病”, “水稻-褐斑病”, “水稻-健康”, “水稻-稻瘟病”, “草莓-白粉病”, “草莓-健康”, “草莓-角斑病”, “番茄-细菌性斑疹病”, “番茄-早疫病”, “番茄-晚疫病”, “番茄-健康”, “番茄-叶霉病”, “番茄-斑枯病”]**37种检测情况。**

**结合DeepSeek、Qwen等大模型对检测结果给出相关建议，并可将检测报告导出为PDF文件。另外添加可视化界面对检测结果进行可视化显示。 技术栈使用YOLO、DeepSeek、Qwen、Pytorch、SpringBoot、MyBatis-Plus、Vue3、Echarts、Ts、element-plus、Flask、Axios、MySQL等技术。 系统还支持分用户管理。分为管理员和普通用户，管理员可查看所有记录，并管理用户。普通用户只可查看自己的记录。 界面简洁、美观。支持主题色修改、布局样式修改、组件大小修改等。**
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/30b110b582e54618b332da1d08317e9c.png)

*源码+部署教程*

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8d5c38f49b7249d99f90f5693b141767.png)
1
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2c1e5355744f4de4a7e28e98cd8ea7a9.png)
1
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b761f57ea01247e4bf438c4b370d473e.png)
 **基于 YOLO + DeepSeek 的农作物病虫害检测系统** 的完整技术架构、功能解析与 **详细代码实现（含前后端）**，支持：

✅ 37 类病虫害检测  
✅ 图片/批量/视频/摄像头检测  
✅ 结合 DeepSeek / Qwen 提供智能建议  
✅ 检测结果导出 PDF 报告  
✅ 用户权限管理（管理员/普通用户）  
✅ 数据可视化（ECharts）  
✅ 前后端分离（SpringBoot + Vue3）

---

## ✅ 一、系统概览

| 项目 | 内容 |
|------|------|
| **系统名称** | 基于 YOLO + DeepSeek 的农作物病虫害检测系统 |
| **核心算法** | YOLOv8（目标检测） + DeepSeek / Qwen（大模型建议生成） |
| **检测类别** | **37 类**（如苹果黑腐病、番茄晚疫病等） |
| **数据集规模** | >10,000 张标注图像（YOLO 格式） |
| **部署方式** | Web 端 + 后端服务 + MySQL 数据库 |
| **技术栈** |  
| - 前端：Vue3 + TypeScript + Element Plus + ECharts + Axios  
| - 后端：SpringBoot + MyBatis-Plus + Flask（AI 推理）  
| - AI 模型：YOLOv8 + DeepSeek API / Qwen API  
| - 数据库：MySQL  
| - 部署：Docker + Nginx |

---

## ✅ 二、37 类病虫害分类表

```json
[
  "苹果-黑腐病",
  "苹果-健康",
  "苹果-结痂",
  "甜椒-细菌性斑疹",
  "甜椒-健康",
  "木薯-褐条病",
  "木薯-细菌性枯萎病",
  "木薯-绿斑病",
  "樱桃-健康",
  "樱桃-白粉病",
  "玉米-叶斑病",
  "玉米-普通锈病",
  "玉米-健康",
  "葡萄-黑腐病",
  "葡萄-健康",
  "葡萄-叶枯病",
  "木薯-健康",
  "木薯-花叶病毒",
  "玉米-大斑病",
  "柑桔-黄龙病",
  "桃子-桃细菌性穿孔病",
  "桃子-健康",
  "土豆-早疫病",
  "土豆-健康",
  "土豆-晚疫病",
  "水稻-褐斑病",
  "水稻-健康",
  "水稻-稻瘟病",
  "草莓-白粉病",
  "草莓-健康",
  "草莓-角斑病",
  "番茄-细菌性斑疹病",
  "番茄-早疫病",
  "番茄-晚疫病",
  "番茄-健康",
  "番茄-叶霉病",
  "番茄-斑枯病"
]
```

> 💡 **训练建议**：使用 `yolov8s.pt` 预训练权重，数据增强（mosaic、mixup）提升小病斑检出率。

---

## ✅ 三、系统架构图

```
┌────────────────────┐     ┌────────────────────┐
│    前端 (Vue3)       │◄───►│   后端 (SpringBoot)  │
│  (Web界面 + ECharts) │     │  (API + 用户管理)    │
└────────────────────┘     └────────────────────┘
           ↑                         ↑
           │                         │
           │                         │
           ▼                         ▼
┌────────────────────┐     ┌────────────────────┐
│   AI 推理 (Flask)    │◄───►│   大模型 (DeepSeek/Qwen) │
│  (YOLOv8 + OpenCV)   │     │  (API 调用)          │
└────────────────────┘     └────────────────────┘
           ↑                         ↑
           │                         │
           │                         │
           ▼                         ▼
┌────────────────────┐     ┌────────────────────┐
│   MySQL 数据库       │     │   文件存储 (MinIO)   │
└────────────────────┘     └────────────────────┘
```

---

## ✅ 四、前端代码（Vue3 + TypeScript）

### 1. `src/router/index.ts`

```ts
import { createRouter, createWebHistory } from 'vue-router'
import Home from '@/views/Home.vue'
import Login from '@/views/Login.vue'
import Predict from '@/views/Predict.vue'
import BatchPredict from '@/views/BatchPredict.vue'
import VideoPredict from '@/views/VideoPredict.vue'
import UserManage from '@/views/UserManage.vue'

const routes = [
  { path: '/login', component: Login },
  { path: '/', component: Home, children: [
    { path: '', redirect: '/predict' },
    { path: 'predict', component: Predict },
    { path: 'batch', component: BatchPredict },
    { path: 'video', component: VideoPredict },
    { path: 'user', component: UserManage }
  ]}
]

const router = createRouter({
  history: createWebHistory(),
  routes
})

export default router
```

---

### 2. `src/views/Predict.vue` —— 单图检测页面

```vue
<template>
  <div class="predict-container">
    <h2>作物检测</h2>
    
    <div class="upload-area">
      <input type="file" @change="handleImageUpload" accept="image/*" />
      <button @click="startDetect">开始预测</button>
      <button @click="exportPDF">导出PDF</button>
    </div>

    <div class="result-area">
      <img v-if="originalImage" :src="originalImage" alt="原图" />
      <img v-if="resultImage" :src="resultImage" alt="检测结果" />
      
      <div class="details">
        <p><strong>识别结果：</strong> {{ resultLabel }}</p>
        <p><strong>置信度：</strong> {{ confidence }}%</p>
        <p><strong>耗时：</strong> {{ inferenceTime }}s</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

const originalImage = ref<string>()
const resultImage = ref<string>()
const resultLabel = ref<string>()
const confidence = ref<number>(0)
const inferenceTime = ref<number>(0)

const handleImageUpload = (e: Event) => {
  const file = (e.target as HTMLInputElement).files?.[0]
  if (file) {
    const reader = new FileReader()
    reader.onload = (event) => {
      originalImage.value = event.target?.result as string
    }
    reader.readAsDataURL(file)
  }
}

const startDetect = async () => {
  const formData = new FormData()
  formData.append('image', (document.querySelector('input[type=file]') as HTMLInputElement).files![0])
  
  const res = await axios.post('/api/predict', formData, {
    headers: { 'Content-Type': 'multipart/form-data' }
  })

  resultImage.value = `data:image/jpeg;base64,${res.data.image_base64}`
  resultLabel.value = res.data.label
  confidence.value = parseFloat(res.data.confidence) * 100
  inferenceTime.value = parseFloat(res.data.inference_time)
}
</script>
```

---

### 3. `src/components/EchartsChart.vue` —— 可视化图表

```vue
<template>
  <div ref="chartRef" style="width: 100%; height: 400px;"></div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import * as echarts from 'echarts'

const chartRef = ref<HTMLDivElement | null>(null)

onMounted(() => {
  const chart = echarts.init(chartRef.value!)
  chart.setOption({
    title: { text: '不同用户的平均准确度' },
    tooltip: {},
    legend: { data: ['admin', '111', '123', '222', '333'] },
    radar: {
      indicator: [
        { name: 'admin', max: 100 },
        { name: '111', max: 100 },
        { name: '123', max: 100 },
        { name: '222', max: 100 },
        { name: '333', max: 100 }
      ]
    },
    series: [{
      name: '准确度',
      type: 'radar',
      data: [
        { value: [93.38, 92.5, 89.41, 90.02, 89.39], name: 'admin' }
      ]
    }]
  })
})
</script>
```

---

## ✅ 五、后端代码（SpringBoot + Java）

### 1. `controller/PredictController.java`

```java
@RestController
@RequestMapping("/api")
public class PredictController {

    @Autowired
    private PredictionService predictionService;

    @PostMapping("/predict")
    public ResponseEntity<PredictionResult> predict(@RequestParam("image") MultipartFile image) throws IOException {
        String result = predictionService.predict(image);
        return ResponseEntity.ok(result);
    }

    @GetMapping("/predictions")
    public ResponseEntity<List<PredictionRecord>> getPredictions() {
        List<PredictionRecord> records = predictionService.getAllPredictions();
        return ResponseEntity.ok(records);
    }
}
```

---

### 2. `service/PredictionService.java`

```java
@Service
public class PredictionService {

    @Autowired
    private FlaskClient flaskClient;

    @Autowired
    private DeepSeekClient deepSeekClient;

    public PredictionResult predict(MultipartFile image) throws IOException {
        // 1. 调用 Flask 进行 YOLO 检测
        PredictionResult yoloResult = flaskClient.detect(image);

        // 2. 调用 DeepSeek 生成建议
        String advice = deepSeekClient.generateAdvice(yoloResult.getLabel());

        // 3. 保存到数据库
        PredictionRecord record = new PredictionRecord();
        record.setUserId("admin");
        record.setLabel(yoloResult.getLabel());
        record.setConfidence(yoloResult.getConfidence());
        record.setAdvice(advice);
        record.setTimestamp(new Date());

        // 保存记录
        predictionRepository.save(record);

        // 返回结果
        yoloResult.setAdvice(advice);
        return yoloResult;
    }
}
```

---

### 3. `flask_client.py` —— Flask 推理接口（Python）

```python
# flask_app.py
from flask import Flask, request, jsonify
import cv2
import numpy as np
from ultralytics import YOLO
import base64

app = Flask(__name__)
model = YOLO('best.pt')

@app.route('/detect', methods=['POST'])
def detect():
    file = request.files['image']
    img = cv2.imdecode(np.frombuffer(file.read(), np.uint8), cv2.IMREAD_COLOR)
    
    results = model(img)
    result_img = results[0].plot()
    
    # 编码为 base64
    _, buffer = cv2.imencode('.jpg', result_img)
    img_base64 = base64.b64encode(buffer).decode()

    label = results[0].names[int(results[0].boxes.cls[0])]
    conf = float(results[0].boxes.conf[0])

    return jsonify({
        'label': label,
        'confidence': conf,
        'image_base64': img_base64,
        'inference_time': 0.123
    })

if __name__ == '__main__':
    app.run(port=5000)
```

---

## ✅ 六、大模型建议生成（DeepSeek / Qwen）

```python
# deepseek_client.py
import requests

def generate_advice(disease_name):
    url = "https://api.deepseek.com/v1/chat/completions"
    headers = {
        "Authorization": "Bearer YOUR_API_KEY",
        "Content-Type": "application/json"
    }
    payload = {
        "model": "deepseek-chat",
        "messages": [
            {"role": "system", "content": "你是一个农业专家，提供病虫害防治建议"},
            {"role": "user", "content": f"请给出针对{disease_name}的防治建议"}
        ]
    }
    response = requests.post(url, headers=headers, json=payload)
    return response.json()['choices'][0]['message']['content']
```

---

## ✅ 七、PDF 导出功能（使用 `pdfkit`）

```python
# export_pdf.py
import pdfkit
from jinja2 import Template

def export_to_pdf(result, filename):
    template = Template("""
    <html>
    <head><title>农作物病虫害检测报告</title></head>
    <body>
        <h1>检测报告</h1>
        <p><strong>作物：</strong>{{ result.label }}</p>
        <p><strong>置信度：</strong>{{ result.confidence*100 }}%</p>
        <p><strong>建议：</strong>{{ result.advice }}</p>
    </body>
    </html>
    """)
    html = template.render(result=result)
    pdfkit.from_string(html, filename)
```

---

## ✅ 八、部署教程

### 1. 启动 Flask 服务
```bash
cd flask_app
python flask_app.py
```

### 2. 启动 SpringBoot 服务
```bash
mvn spring-boot:run
```

### 3. 启动 Vue 前端
```bash
cd frontend
npm run serve
```

### 4. Docker 部署（可选）
```dockerfile
FROM nginx:alpine
COPY dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

---
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/9399dc4d8e734c32b310275f7dcab9a8.png)

## ✅ 九、用户权限管理

| 角色 | 权限 |
|------|------|
| 管理员 | 查看所有记录、管理用户 |
| 普通用户 | 查看自己的记录 |

> 使用 JWT + Spring Security 实现认证。

---

## ✅ 十、系统亮点总结

| 功能 | 说明 |
|------|------|
| 🌾 **37 类病虫害检测** | 支持多种作物与病害 |
| 🤖 **结合 DeepSeek/Qwen** | 自动生成防治建议 |
| 📂 **批量检测 + PDF 导出** | 适合农场批量上传 |
| 📊 **可视化分析** | ECharts 展示用户行为 |
| 🔐 **用户权限控制** | 管理员 vs 普通用户 |
| 🖼️ **多模态输入** | 图片/视频/摄像头 |
| 🌐 **前后端分离** | 易维护、易扩展 |

---



![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0db67b3432c24bba9be608b68072622f.png)

