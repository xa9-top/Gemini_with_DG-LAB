# Gemini_with_DG-LAB

本项目灵感来源于B站视频 BV1oaFoe7EoN

## 特性喵~

- **猫娘调教**: 你将扮演成一只可爱的猫娘， Gemini AI 会与你进行互动喵~
- **DG-LAB 设备控制**: 通过 AI 输出的指令控制 DG-LAB 设备的A、B通道的强度和波形喵~
- **多种波形预设**: 内置多种预设波形，让互动更加丰富有趣喵~
- **动态强度调整**: AI 可根据对话情境动态调整设备强度喵~

## 配置环境喵~

在运行本项目之前，请确保你已经准备好以下物品并完成相关配置：

1. **Python 3.9+ 环境**: 推荐使用 Python 3.9 或更高版本喵~
2. **郊狼3.0**: 确保你的设备可以正常工作喵~
3. **DG-LAB APP**: 在你的手机上安装 DG-LAB APP，用于连接设备喵~
4. **Gemini API Key**: 在 https://makersuite.google.com/app/apikey 获取你的 Gemini API Key 喵~

## 配置环境喵~

1. 克隆本项目到你的本地喵~

   Bash

   ```bash
   git clone https://github.com/xa9-top/Gemini_with_DG-LAB.git
   cd Gemini_with_DG-LAB
   ```

2. 安装所需的Python库喵~

   ```bash
   pip install -r requestments.txt
   ```

## 配置代码喵~

在运行代码之前，你需要修改文件中的几处配置喵~

打开 `play.py` 文件，找到并修改以下内容：

1. **代理IP服务器**: 如果你需要设置HTTP代理，请修改第27行。如果不需要，可以注释掉这一行喵~

   ```python
   os.environ["HTTPS_PROXY"] = "http://localhost:7897" # 设置代理(HTTP代理)喵~ (如果不需要代理就注释掉这一行喵~)
   ```

2. **通道强度软上限**: 修改第32-33行，设置A通道和B通道的软上限（0-100之间），这会影响Gemini给出强度的缩放喵~

   ```python
   strength_limit_a_set = 100
   strength_limit_b_set = 100
   ```

3. **AI API 配置**: 修改第37-39行，填入你的API Key。如果有需要，可以修改 `base_url` 来兼容其他与 OpenAI 格式兼容的服务提供商喵~ 

   ```python
   # 初始化Gemini API喵~
   aiclient = openai.OpenAI(
       api_key="API-KEY", # 这里填Gemini api，在 https://makersuite.google.com/app/apikey 获取喵~
       base_url="https://generativelanguage.googleapis.com/v1beta/openai/" # 如果使用其他兼容OpenAI的服务商，请修改为对应的API地址喵~
   )
   ```

4. **局域网IP地址**: 在第42行填入你的局域网IP地址和websocket端口，用于DG-LAB APP连接喵~

   ```python
   ws_client_url = "ws://192.168.0.10:9090" # 这里填局域网ip地址和websocket端口喵~ (ws://ip:port)喵~
   ```

5. **修改提示词 (可选)**: 如果你想修改Gemini的提示词，可以在第307行进行修改喵~

   ```
   # 修改提示词在第307行喵~
   # ...
   # {"role": "system", "content": '''...'''}[...]
   ```

## 运行喵~

完成配置后，你就可以运行项目了喵~

```shell
python play.py
```

运行后，程序会生成一个二维码，请使用 DG-LAB APP 扫描二维码进行连接喵~

## 使用喵~

连接成功后，你就可以在终端与Gemini进行对话了喵~ AI会根据你的对话内容，输出相应的DG-LAB设备控制指令，并自动发送给设备喵~

你可以输入 `/quit` 来退出程序喵~

## 注意事项喵~

- 请确保你的设备和运行程序的电脑在同一个局域网内喵~
- 本项目的AI控制功能仅供娱乐和学习使用，请注意安全，并遵守当地法律法规喵~
- 如果你遇到连接问题，请检查防火墙设置或代理配置喵~

## 贡献喵~

如果你有任何建议或想贡献代码，欢迎提交 Pull Request 喵~

## 许可证喵~

本项目采用 MIT 许可证喵~



byd用Gemini写的readme好难绷喵~