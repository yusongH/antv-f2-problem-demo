<template>
  <div>
    <canvas id="myChart2" width="375" height="260"></canvas>
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
          year: "1951-01",
          sales: 38,
        },
        {
          year: "1952-01",
          sales: 52,
        },
        {
          year: "1956-01",
          sales: 61,
        },
        {
          year: "1957-01",
          sales: 145,
        },
        {
          year: "1958-01",
          sales: 48,
        },
        {
          year: "1959-01",
          sales: 38,
        },
        {
          year: "1960-01",
          sales: 38,
        },
        {
          year: "1962-01",
          sales: 38,
        },
      ],
    };
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const chart = new F2.Chart({
        id: "myChart2",
        pixelRatio: window.devicePixelRatio, // 指定分辨率
      });

      chart.source(this.chartData, {
        year: {
          type: 'timeCat',
          tickCount: 5,
        },
      });
      chart.tooltip({
        showItemMarker: false,
        onShow: function onShow(ev) {
          const items = ev.items;
          items[0].name = null;
          items[0].name = items[0].title;
          items[0].value = "¥ " + items[0].value;
        },
      });
      chart.interval().position("year*sales").color('l(-90) 0.03:rgba(216,216,216,0.10) 1:#6E6CD8');

      chart.render();
    },
  },
};
</script>

<style></style>
