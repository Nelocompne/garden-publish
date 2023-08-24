public:: true
date:: "2022-11-14"

- ```
  magnet:?xt=urn:btih:lppeilnimjs3m4fd4xvdcy5pvuwg7dwm&dn=novelaileak&xl=55901742348&fc=94
  magnet:?xt=urn:btih:uiaipz4ap4ueo3oxwczoaf2jqfyj3con&dn=novelaileakpt2&xl=133721477323&fc=573
  ```
- set
	- step >= 28
	- cfg scale = 11
- ## 在线部署
- https://www.bilibili.com/video/BV1JG4y1p7hT
	- https://aistudio.baidu.com/aistudio/projectdetail/4666819?channel=0&channelType=0&sUid=62729&shared=1&ts=1665318335360
- https://t.me/StableDiffusion_CN/9763
	- https://colab.research.google.com/drive/1zuK0u8UW8IKMEvVNz7lU34Qph_gS14XD
- ## 本地部署
- ![image.png](../assets/image_1692612286824_0.png)
- ## prompt
- `{{masterpiece}}, {best quality}, {high quality}, highly detailed`
- `(masterpiece:1.16), (best quality:1.05), (highly detailed:1.05)`
- ## negative prompt
- `lowres, bad anatomy, {{bad hands}}, text, error, {{missing fingers}}, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blurry`
- `lowres, bad anatomy, (bad hand), text, error, (missing fingers), extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blurry`
- ## 参考来源
- https://rentry.co/voldy
- https://rentry.org/sdg_FAQ
- ### What does ()/[]/{} or (word:number) mean?
- `()` adds emphasis to a term, `[]` decreases emphasis, both by a factor of 1.1. You can either stack `()`/`[]` for increasing/decreasing emphasis or use the new syntax which takes a number directly - it looks like this:
- ```
  (word:1.1) == (word)
  (word:1.21) == ((word))
  (word:0.91) == [word]
  ```
- To use literal `()`/`[]` in your prompt, escape them with \
  See https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features for full details and additional features.
- `{word}` is for NovelAI's official service only. It is similar to `(word)` but the emphasis is only increased by a factor of 1.05. If you are using the leaked models in the webui you shouldn't be using this syntax.
- ### APPROXIMATE RENDER TIME BY GPU (50 steps)
- ![](https://i.ibb.co/5GwFS7Z/chartthin.png)