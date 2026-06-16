<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>純前端超微型 LLM 測試</title>
    <style>
        body { font-family: system-ui, sans-serif; max-width: 500px; margin: 50px auto; padding: 20px; text-align: center; }
        input { width: 80%; padding: 12px; font-size: 16px; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 4px; }
        button { padding: 12px 24px; font-size: 16px; cursor: pointer; background: #FF9900; color: white; border: none; border-radius: 4px; font-weight: bold; }
        button:disabled { background: #ccc; cursor: not-allowed; }
        #status { font-weight: bold; color: #666; margin: 15px 0; background: #fff3cd; padding: 10px; border-radius: 4px; }
        #chatbox { margin-top: 30px; padding: 20px; background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 6px; text-align: left; min-height: 60px; line-height: 1.5; }
    </style>
</head>
<body>

    <h2>🤖 100% 本地 LLM 模型對話測試</h2>
    <p>完全不用 API Key。Say Hi 測試專用版。</p>

    <div id="status">正在初始環境中... 請稍候...</div>

    <input type="text" id="userInput" value="Hi" placeholder="同 AI 講句嘢...">
    <br>
    <button id="sendBtn" onclick="generateText()" disabled>等待 AI 準備就緒</button>

    <div id="chatbox"><b>AI 真實回覆：</b> <br><span id="aiReply">等待發送指令...</span></div>

    <script type="module">
        // 2. 修正為正版官方路徑
        import { pipeline, env } from 'https://cdn.jsdelivr.net/npm/@huggingface/transformers@3.0.0-alpha.5';

        // 3. 終極安全設定，防止被 Hugging Face 的 iframe 沙盒封殺
        env.backends.onnx.wasm.numThreads = 1; 
        env.backends.onnx.wasm.proxy = false;     
        env.allowLocalModels = false; 

        let generator = null;
        const statusDiv = document.getElementById('status');
        const sendBtn = document.getElementById('sendBtn');
        const outputDiv = document.getElementById('aiReply'); // 修正為直接對應回覆內容的 ID

        // 4. 初始化 AI 函數
        async function initAI() {
            try {
                statusDiv.innerText = "正在下載並載入 AI 模型 (SmolLM2-360M)...";
                
                // 優先使用 WebGPU，如果失敗會觸發 catch 自動轉向 WASM (CPU)
                generator = await pipeline('text-generation', 'HuggingFaceTB/SmolLM2-360M-Instruct', {
                    device: 'webgpu'
                });
                
                statusDiv.innerText = "✅ AI 模型已成功載入 (WebGPU 加速)！";
                statusDiv.style.backgroundColor = "#d4edda";
                statusDiv.style.color = "#155724";
                sendBtn.disabled = false;
                sendBtn.innerText = "叫 AI 回覆";
            } catch (err) {
                console.log("WebGPU 啟動失敗，正在切換至 CPU (WASM) 安全模式...", err);
                try {
                    // 安全備用方案
                    generator = await pipeline('text-generation', 'HuggingFaceTB/SmolLM2-360M-Instruct', {
                        device: 'wasm'
                    });
                    statusDiv.innerText = "✅ AI 模型已成功載入 (CPU 安全模式)！";
                    statusDiv.style.backgroundColor = "#d4edda";
                    statusDiv.style.color = "#155724";
                    sendBtn.disabled = false;
                    sendBtn.innerText = "叫 AI 回覆";
                } catch (cpuErr) {
                    console.error("模型載入徹底失敗:", cpuErr);
                    statusDiv.innerText = "❌ 載入徹底出錯: " + (cpuErr ? cpuErr.message : "未知錯誤");
                    statusDiv.style.backgroundColor = "#f8d7da";
                }
            }
        }

        // 5. 處理對話生成函數 (綁定到全域 window 確保 HTML onclick 找得到)
        window.generateText = async function() {
            const input = document.getElementById('userInput').value;
            if (!input) return alert("請輸入內容");

            sendBtn.disabled = true;
            sendBtn.innerText = "AI 思考中...";
            outputDiv.innerText = "AI 正在用你部電腦嘅硬件計算緊...";

            try {
                const messages = [{ role: "user", content: input }];
                
                const response = await generator(messages, { 
                    max_new_tokens: 30,
                    temperature: 0.7
                });

                // 正確抓取並顯示對話內容
                outputDiv.innerText = response[0].generated_text[messages.length].content;
            } catch (err) {
                outputDiv.innerText = "❌ 生成失敗: " + err.message;
            } finally {
                sendBtn.disabled = false;
                sendBtn.innerText = "叫 AI 回覆";
            }
        }

        // 6. 網頁加載完畢後自動觸發 AI 初始化
        initAI();
    </script>
</body>
</html>
