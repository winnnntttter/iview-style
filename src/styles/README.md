# 样式库说明

## 目录

|-- animation  (动画)

|-- common  (全局样式)

|-- components  (组件样式)

|-- mixins  (混入)

## 修改项：

### 颜色
1. 使用arco-design的梯度算法，老的算法在colorPalette-old.less备份
2. 主色、信息、成功、警告、错误色按钮的hover和active使用颜色梯度5和7
3. less常用color方法：
    - mix 混合颜色，算法：
        ```JavaScript
        function mix(color1, color2, weight) {
          if (!weight) {
            weight = '50%';
          }
          var p = parseFloat(weight) / 100.0;
          var w = p * 2 - 1;
          var a = color1.a - color2.a;
          var w1 = (((w * a == -1) ? w : (w + a) / (1 + w * a)) + 1) / 2.0;
          var w2 = 1 - w1;
          var rgb = [
            Math.round(color1.r * w1 + color2.r * w2),
            Math.round(color1.g * w1 + color2.g * w2),
            Math.round(color1.b * w1 + color2.b * w2)
          ];
          var alpha = color1.a * p + color2.a * (1 - p);
          return 'rgba(' + rgb.join(',') + ',' + alpha + ')';
        }
        console.log(mix({ r: 100, g: 0, b: 0, a: 0.5 }, { r: 100, g: 0, b: 100, a: 0.5 }, '25%'));
        // rgba(100,0,75,0.5)
        ```
    - tint 用于通过提供颜色和白色之间的百分比来混合。 0％是纯色，100％是白色。大致算法：
    - shade 用于通过提供颜色和黑色之间的百分比来混合。 0％是纯色，100％是黑色。
    - fade 透明度绝对值
    - saturate HSL 的S饱和度增加
    - desaturate HSL 的S饱和度减少
    - spin HSL 的H色相旋转
    - lighten HSL 的L亮度增加
    - darken HSL 的L亮度减少