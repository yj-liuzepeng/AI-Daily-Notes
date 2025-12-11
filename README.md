# AI-Daily-Notes

1. 大模型推理/生成阶段的两个参数 temperature 和 top-p：大模型在推理生成时，其实就是根据概率预测下一个词，模型输出的是一组原始分数（Logits），在转化为概率（Softmax）之前，会把这些分数除以 temperature (T)，从而**控制输出概率**，temperature越小，输出相对越稳定，temperature越大，输出相对就会发散 ，就如这个词意温度一样，水低温时稳定成固态，高温时不稳定会挥发。top-p控制的也是输出的概率，越小，输出越保守，越稳定，越大输出的答案越发散。推荐只用一种即可，一句话描述： temperature 熵增熵减，top-p 去尾。（8.97 复制打开抖音，看看【马克的技术工作坊的作品】Temperature & Top-p：大模型的创... https://v.douyin.com/GgkLeHOHKXI/ r@E.uF 12/05 OKw:/ ）
