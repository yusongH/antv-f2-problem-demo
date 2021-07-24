<template>
  <div>
    <canvas id="myChart" width="375" height="260"></canvas>
  </div>
</template>

<script>
import F2 from "@antv/f2";

export default {
  name: "AntvF2Demo",
  data() {
    return {
      chartData: [
        {
          date: "2017/06",
          value: 116,
        },
        {
          date: "2017/07",
          value: 129,
        },
        {
          date: "2017/08",
          value: 135,
        },
        {
          date: "2017/09",
          value: 86,
        }
      ]
    };
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const chart = new F2.Chart({
        id: "myChart",
        pixelRatio: window.devicePixelRatio, // 指定分辨率
      });

      chart.source(this.chartData, {
        value: {
          tickCount: 5,
          min: 0,
        },
        date: {
          type: "timeCat",
          range: [0, 1],
          tickCount: 3,
        },
      });
      chart.tooltip({
        custom: true,
        showXTip: true,
        showYTip: true,
        snap: true,
        crosshairsType: "xy",
        crosshairsStyle: {
          lineDash: [2],
        },
      });
      chart.axis("date", {
        label: function label(text, index, total) {
          const textCfg = {};
          if (index === 0) {
            textCfg.textAlign = "left";
          } else if (index === total - 1) {
            textCfg.textAlign = "right";
          }
          return textCfg;
        },
      });
      chart.line().position("date*value");

      chart.render();
    },
  },
};
</script>

<style></style>
