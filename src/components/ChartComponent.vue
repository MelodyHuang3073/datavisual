<template>
  <div class="drama-charts">
    <h2>2025年電視劇集抖音單話題播放量排名</h2>
    
    <div class="chart-container-wrapper">
      <div class="chart-section" ref="totalViewsSection" id="totalViews">
        <h3>TOP15 電視劇總播放量(億)</h3>
        <div class="chart-content" ref="totalViewsChart"></div>
      </div>
      
      <div class="chart-section" ref="growthSection" id="growth">
        <h3>TOP15 播放量增長分析(億)</h3>
        <div class="chart-content" ref="growthChart"></div>
      </div>
      
      <div class="chart-section" ref="platformSection" id="platform">
        <h3>各平台總播放量佔比</h3>
        <div class="chart-content" ref="platformChart"></div>
      </div>
      
      <div class="chart-section" ref="durationSection" id="duration">
        <h3>播出天數與總播放量關係</h3>
        <div class="chart-content" ref="durationChart"></div>
      </div>
    </div>
    
    <div class="data-table-section" ref="tableSection" id="table">
      <h3>完整數據表格</h3>
      <div class="data-table">
        <table>
          <thead>
            <tr>
              <th>排名</th>
              <th>播出天數</th>
              <th>播出平台</th>
              <th>劇名</th>
              <th>總播放量(億)</th>
              <th>開播時</th>
              <th>開播後增長</th>
              <th>完結時</th>
              <th>完結後增長</th>
              <th>V30</th>
              <th>V30增長</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(drama, index) in dramas" :key="index">
              <td>{{ index + 1 }}</td>
              <td>{{ drama.days }}</td>
              <td>{{ drama.platform }}</td>
              <td>{{ drama.name }}</td>
              <td>{{ drama.totalViews }}</td>
              <td>{{ drama.startViews }}</td>
              <td>{{ drama.growthAfterStart }}</td>
              <td>{{ drama.endViews }}</td>
              <td>{{ drama.growthAfterEnd }}</td>
              <td>{{ drama.v30 }}</td>
              <td>{{ drama.v30Growth }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts';

export default {
  name: 'DramaCharts',
  data() {
    return {
      dramas: [
        { rank: 1, days: 34, platform: '優酷', name: '難哄', totalViews: 228.4, startViews: 67.8, growthAfterStart: 160.6, endViews: 210.4, growthAfterEnd: 18.0, v30: 227.7, v30Growth: 0.7 },
        { rank: 2, days: 82, platform: '愛奇藝', name: '白月梵星', totalViews: 182.4, startViews: 27.0, growthAfterStart: 155.4, endViews: 144.1, growthAfterEnd: 38.3, v30: 175.4, v30Growth: 7.0 },
        { rank: 3, days: 83, platform: '芒果TV', name: '國色芳華', totalViews: 161.5, startViews: 20.3, growthAfterStart: 141.2, endViews: 134.7, growthAfterEnd: 26.8, v30: 155.7, v30Growth: 5.8 },
        { rank: 4, days: 52, platform: '騰訊視頻', name: '六姊妹', totalViews: 115.9, startViews: 5.3, growthAfterStart: 110.6, endViews: 98.0, growthAfterEnd: 18.0, v30: 114.9, v30Growth: 1.0 },
        { rank: 5, days: 63, platform: '芒果TV', name: '五福臨門', totalViews: 96.2, startViews: 13.8, growthAfterStart: 82.4, endViews: 79.9, growthAfterEnd: 16.3, v30: 93.8, v30Growth: 2.4 },
        { rank: 6, days: 85, platform: '騰訊視頻', name: '大奉打更人', totalViews: 92.4, startViews: 20.7, growthAfterStart: 71.7, endViews: 81.5, growthAfterEnd: 10.9, v30: 90.2, v30Growth: 2.2 },
        { rank: 7, days: 11, platform: '騰訊視頻', name: '雁回時', totalViews: 86.7, startViews: 1.3, growthAfterStart: 85.4, endViews: 79.8, growthAfterEnd: 6.9, v30: 86.7, v30Growth: 0 },
        { rank: 8, days: 60, platform: '愛奇藝', name: '白色橄欖樹', totalViews: 75.7, startViews: 23.5, growthAfterStart: 52.2, endViews: 64.0, growthAfterEnd: 11.8, v30: 74.4, v30Growth: 1.3 },
        { rank: 9, days: 22, platform: '優酷', name: '噓，國王在冬眠', totalViews: 70.8, startViews: 21.8, growthAfterStart: 49.0, endViews: 63.5, growthAfterEnd: 7.3, v30: 70.8, v30Growth: 0 },
        { rank: 10, days: 85, platform: '愛奇藝', name: '漂白', totalViews: 64.3, startViews: 1.2, growthAfterStart: 63.1, endViews: 55.1, growthAfterEnd: 9.2, v30: 63.7, v30Growth: 0.6 },
        { rank: 11, days: 29, platform: '芒果TV', name: '雲之羽', totalViews: 60.6, startViews: 15.6, growthAfterStart: 45.0, endViews: 55.3, growthAfterEnd: 5.3, v30: 60.6, v30Growth: 0 },
        { rank: 12, days: 50, platform: '愛奇藝', name: '安娜的愛人', totalViews: 55.5, startViews: 10.8, growthAfterStart: 44.7, endViews: 49.6, growthAfterEnd: 5.9, v30: 54.7, v30Growth: 0.8 },
        { rank: 13, days: 30, platform: '優酷', name: '流光之下', totalViews: 51.2, startViews: 8.3, growthAfterStart: 42.9, endViews: 47.5, growthAfterEnd: 3.7, v30: 51.2, v30Growth: 0 },
        { rank: 14, days: 74, platform: '騰訊視頻', name: '愛的邊疆', totalViews: 50.4, startViews: 6.1, growthAfterStart: 44.3, endViews: 45.0, growthAfterEnd: 5.4, v30: 48.7, v30Growth: 1.7 },
        { rank: 15, days: 80, platform: '芒果TV', name: '星落凝成糖', totalViews: 48.3, startViews: 5.6, growthAfterStart: 42.7, endViews: 43.9, growthAfterEnd: 4.4, v30: 47.2, v30Growth: 1.1 }
      ],
      charts: [],
      selectedChart: 'all',
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.initCharts();
      window.addEventListener('resize', this.handleResize);
      window.addEventListener('wheel', this.handleWheel, { passive: false });
    });
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize);
    window.removeEventListener('wheel', this.handleWheel);
    this.charts.forEach(chart => chart.dispose());
  },
  methods: {
    handleResize() {
      this.charts.forEach(chart => chart.resize());
    },
    handleWheel(event) {
      if (event.ctrlKey) {
        event.preventDefault();
      }
    },
    scrollToChart() {
      if (this.selectedChart === 'all') {
        window.scrollTo({ top: 0, behavior: 'smooth' });
      } else if (this.selectedChart === 'table') {
        this.$refs.tableSection.scrollIntoView({ behavior: 'smooth' });
      } else {
        const section = this.$refs[`${this.selectedChart}Section`];
        if (section) {
          section.scrollIntoView({ behavior: 'smooth' });
        }
      }
    },
    initCharts() {
      this.charts = [
        this.initTotalViewsChart(),
        this.initGrowthChart(),
        this.initPlatformChart(),
        this.initDurationChart()
      ];
    },
    initTotalViewsChart() {
      const chart = echarts.init(this.$refs.totalViewsChart);
      const top15 = [...this.dramas].slice(0, 15);

      const option = {
        tooltip: {
          trigger: 'axis',
          axisPointer: { 
            type: 'shadow',
            shadowStyle: {
              color: 'rgba(0, 0, 0, 0.1)'
            }
          },
          backgroundColor: 'rgba(255, 255, 255, 0.95)',
          borderColor: '#eee',
          borderWidth: 1,
          padding: [10, 15],
          textStyle: {
            color: '#333'
          },
          formatter(params) {
            const data = params[0].data;
            return `
              <div style="font-weight:bold;margin-bottom:5px">${data.name}</div>
              <div>平台: <span style="color:${getPlatformColor(data.platform)}">${data.platform}</span></div>
              <div>播出天數: ${data.days}天</div>
            `;
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '10%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          data: top15.map(d => d.name),
          axisLine: {
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          axisLabel: { 
            rotate: 45, 
            interval: 0,
            color: '#666',
            fontSize: 12
          }
        },
        yAxis: { 
          type: 'value', 
          name: '播放量(億)',
          nameTextStyle: {
            color: '#666',
            padding: [0, 0, 0, 40]
          },
          axisLine: {
            show: true,
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          splitLine: {
            lineStyle: {
              color: '#f5f5f5'
            }
          },
          axisLabel: {
            color: '#666'
          }
        },
        series: [{
          name: '總播放量',
          type: 'bar',
          barWidth: '60%',
          data: top15.map(d => ({ 
            value: d.totalViews, 
            name: d.name, 
            platform: d.platform, 
            days: d.days 
          })),
          itemStyle: {
            color: ({ data }) => getPlatformColor(data.platform),
            borderRadius: [4, 4, 0, 0],
            shadowColor: 'rgba(0, 0, 0, 0.1)',
            shadowBlur: 5,
            shadowOffsetY: 2
          },
          emphasis: {
            itemStyle: {
              shadowColor: 'rgba(0, 0, 0, 0.2)',
              shadowBlur: 10,
              shadowOffsetY: 5
            }
          },
          label: { 
            show: true, 
            position: 'top', 
            formatter: '{c}億',
            color: '#333',
            fontWeight: 'bold'
          },
          animationType: 'scale',
          animationEasing: 'elasticOut',
          animationDelay: function (idx) {
            return idx * 100;
          }
        }]
      };

      chart.setOption(option);
      return chart;
    },

    initGrowthChart() {
      const chart = echarts.init(this.$refs.growthChart);
      const top15 = this.dramas.slice(0, 15);

      const option = {
        tooltip: {
          trigger: 'axis',
          axisPointer: { 
            type: 'shadow',
            shadowStyle: {
              color: 'rgba(0, 0, 0, 0.1)'
            }
          },
          backgroundColor: 'rgba(255, 255, 255, 0.95)',
          borderColor: '#eee',
          borderWidth: 1,
          padding: [10, 15],
          textStyle: {
            color: '#333'
          },
          formatter(params) {
            const data = top15[params[0].dataIndex];
            let result = `
              <div style="font-weight:bold;margin-bottom:5px">${data.name}</div>
              <div>平台: <span style="color:${getPlatformColor(data.platform)}">${data.platform}</span></div>
            `;
            
            params.forEach(p => {
              const percent = Math.round(p.value / data.totalViews * 100);
              result += `
                <div style="margin-top:3px">
                  ${p.seriesName}: 
                  <span style="font-weight:bold">${p.value}億</span> 
                  <span style="color:#888">(${percent}%)</span>
                </div>
              `;
            });
            
            result += `
              <div style="margin-top:8px;font-size:16px;font-weight:bold;color:#2c7be5">
                總播放量: ${data.totalViews}億
              </div>
            `;
            return result;
          }
        },
        legend: { 
          data: ['開播時', '開播後增長', '完結後增長'], 
          bottom: 0,
          textStyle: {
            color: '#666'
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '15%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          data: top15.map(d => d.name),
          axisLine: {
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          axisLabel: { 
            rotate: 45, 
            interval: 0,
            color: '#666',
            fontSize: 12
          }
        },
        yAxis: { 
          type: 'value', 
          name: '播放量(億)',
          nameTextStyle: {
            color: '#666',
            padding: [0, 0, 0, 40]
          },
          axisLine: {
            show: true,
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          splitLine: {
            lineStyle: {
              color: '#f5f5f5'
            }
          },
          axisLabel: {
            color: '#666'
          }
        },
        series: [
          {
            name: '開播時',
            type: 'bar',
            stack: 'total',
            data: top15.map(d => d.startViews),
            itemStyle: {
              color: '#5470C6',
              borderRadius: [4, 4, 0, 0],
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 5,
              shadowOffsetY: 2
            },
            emphasis: {
              itemStyle: {
                shadowColor: 'rgba(0, 0, 0, 0.2)',
                shadowBlur: 10,
                shadowOffsetY: 5
              }
            },
            animationType: 'scale',
            animationEasing: 'elasticOut'
          },
          {
            name: '開播後增長',
            type: 'bar',
            stack: 'total',
            data: top15.map(d => d.growthAfterStart),
            itemStyle: {
              color: '#91CC75',
              borderRadius: [4, 4, 0, 0],
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 5,
              shadowOffsetY: 2
            },
            emphasis: {
              itemStyle: {
                shadowColor: 'rgba(0, 0, 0, 0.2)',
                shadowBlur: 10,
                shadowOffsetY: 5
              }
            },
            animationType: 'scale',
            animationEasing: 'elasticOut',
            animationDelay: function (idx) {
              return idx * 50 + 100;
            }
          },
          {
            name: '完結後增長',
            type: 'bar',
            stack: 'total',
            data: top15.map(d => d.growthAfterEnd),
            itemStyle: {
              color: '#FAC858',
              borderRadius: [4, 4, 0, 0],
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 5,
              shadowOffsetY: 2
            },
            emphasis: {
              itemStyle: {
                shadowColor: 'rgba(0, 0, 0, 0.2)',
                shadowBlur: 10,
                shadowOffsetY: 5
              }
            },
            animationType: 'scale',
            animationEasing: 'elasticOut',
            animationDelay: function (idx) {
              return idx * 50 + 150;
            }
          }
        ]
      };

      chart.setOption(option);
      return chart;
    },
    
    initPlatformChart() {
      const chart = echarts.init(this.$refs.platformChart);
      const platformMap = {};
      this.dramas.forEach(drama => {
        platformMap[drama.platform] = (platformMap[drama.platform] || 0) + drama.totalViews;
      });

      const option = {
        tooltip: { 
          trigger: 'item', 
          backgroundColor: 'rgba(255, 255, 255, 0.95)',
          borderColor: '#eee',
          borderWidth: 1,
          textStyle: {
            color: '#333'
          },
          formatter: '{a} <br/>{b}: {c}億 ({d}%)' 
        },
        legend: { 
          orient: 'vertical', 
          right: 10, 
          top: 'center',
          textStyle: {
            color: '#666'
          }
        },
        series: [{
          name: '平台分布',
          type: 'pie',
          radius: ['45%', '75%'],
          center: ['40%', '50%'],
          avoidLabelOverlap: false,
          label: { 
            show: false
          },
          emphasis: {
            scale: true,
            scaleSize: 10,
            label: {
              show: true,
              fontSize: '16',
              fontWeight: 'bold',
              formatter: '{b}\n{c}億 ({d}%)',
              color: '#333'
            }
          },
          labelLine: { 
            show: false 
          },
          data: Object.entries(platformMap).map(([name, value]) => ({ 
            name, 
            value,
            itemStyle: {
              color: getPlatformColor(name),
              shadowColor: 'rgba(0, 0, 0, 0.2)',
              shadowBlur: 10,
              shadowOffsetY: 3
            }
          })),
          roseType: 'radius',
          animationType: 'scale',
          animationEasing: 'elasticOut',
          animationDelay: function (idx) {
            return idx * 100;
          }
        }],
        graphic: {
          type: 'text',
          left: 'center',
          top: '85%',
          style: {
            text: '總播放量: ' + this.dramas.reduce((sum, d) => sum + d.totalViews, 0).toFixed(1) + '億',
            fontSize: 14,
            fontWeight: 'bold',
            fill: '#333'
          }
        }
      };

      chart.setOption(option);
      return chart;
    },
    
    initDurationChart() {
      const chart = echarts.init(this.$refs.durationChart);
      const data = this.dramas.filter(d => d.days && d.totalViews);

      const option = {
        tooltip: {
          trigger: 'item',
          backgroundColor: 'rgba(255, 255, 255, 0.95)',
          borderColor: '#eee',
          borderWidth: 1,
          padding: [10, 15],
          textStyle: {
            color: '#333'
          },
          formatter(params) {
            const d = params.data;
            return `
              <div style="font-weight:bold;margin-bottom:5px">${d[2]}</div>
              <div>平台: <span style="color:${getPlatformColor(d[3])}">${d[3]}</span></div>
              <div>播出天數: ${d[0]}天</div>
              <div style="margin-top:5px;font-size:16px;font-weight:bold;color:#2c7be5">
                總播放量: ${d[1]}億
              </div>
            `;
          }
        },
        grid: {
          left: '10%',
          right: '5%',
          top: '15%',
          bottom: '10%'
        },
        xAxis: { 
          type: 'value', 
          name: '播出天數',
          nameTextStyle: {
            color: '#666',
            padding: [0, 0, 0, 40]
          },
          axisLine: {
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          splitLine: {
            lineStyle: {
              color: '#f5f5f5'
            }
          },
          axisLabel: {
            color: '#666'
          }
        },
        yAxis: {
          type: 'value',
          name: '總播放量(億)',
          nameTextStyle: {
            color: '#666'
          },
          axisLine: {
            lineStyle: {
              color: '#e0e0e0'
            }
          },
          splitLine: {
            lineStyle: {
              color: '#f5f5f5'
            }
          },
          axisLabel: {
            color: '#666'
          }
        },
        visualMap: {
          min: 40,
          max: 230,
          dimension: 1,
          inRange: {
            color: ['#50a3ba', '#eac736', '#d94e5d']
          },
          textStyle: {
            color: '#666'
          },
          right: 10,
          top: 'center'
        },
        series: [{
          name: '電視劇',
          type: 'scatter',
          symbolSize: d => Math.sqrt(d[1]) * 2.5,
          data: data.map(d => [d.days, d.totalViews, d.name, d.platform]),
          itemStyle: {
            color: ({ data }) => getPlatformColor(data[3]),
            shadowColor: 'rgba(0, 0, 0, 0.2)',
            shadowBlur: 5,
            shadowOffsetY: 3
          },
          emphasis: {
            itemStyle: {
              shadowColor: 'rgba(0, 0, 0, 0.4)',
              shadowBlur: 10,
              shadowOffsetY: 5
            }
          },
          animationType: 'scale',
          animationEasing: 'elasticOut',
          animationDelay: function (idx) {
            return idx * 50;
          }
        }]
      };

      chart.setOption(option);
      return chart;
    }
  }
};

function getPlatformColor(platform) {
  const colorMap = {
    '騰訊視頻': '#00a1d6',
    '愛奇藝': '#29b078',
    '優酷': '#f85959',
    '芒果TV': '#ff7f00'
  };
  return colorMap[platform] || '#c23531';
}
</script>

<style scoped>

html, body {
  height: 100%; 
  overflow-x: hidden; 
  overflow-y: visible; 
  margin: 0;
  padding: 0;
}

.drama-charts {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 30px 20px;
  font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background-color: #f9fafc;
  height: auto;
}

h2 {
  text-align: center;
  margin-bottom: 30px;
  color: #2c3e50;
  font-size: 26px;
  font-weight: 600;
  letter-spacing: 1px;
}

h3 {
  text-align: center;
  margin: 20px 0 15px;
  color: #34495e;
  font-size: 20px;
  font-weight: 500;
}

.chart-controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
  padding: 0 10px;
}

.chart-selector {
  display: flex;
  align-items: center;
}

.chart-selector label {
  margin-right: 10px;
  font-weight: 500;
  color: #2c3e50;
}

.chart-selector select {
  padding: 8px 15px;
  border-radius: 6px;
  border: 1px solid #ddd;
  background-color: white;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.2s;
}

.chart-selector select:hover {
  border-color: #bbb;
}

.chart-selector select:focus {
  outline: none;
  border-color: #2c7be5;
  box-shadow: 0 0 0 2px rgba(44, 123, 229, 0.2);
}

.zoom-controls {
  display: flex;
  align-items: center;
  gap: 10px;
}

.zoom-controls button {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 1px solid #ddd;
  background-color: white;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
}

.zoom-controls button:hover {
  background-color: #f5f5f5;
}

.zoom-controls button:active {
  background-color: #eee;
}

.zoom-controls span {
  min-width: 40px;
  text-align: center;
  font-weight: 500;
}

.chart-container-wrapper {
  transform-origin: top center;
  transition: transform 0.2s ease;
  width: 100%;
  height: auto;
  will-change: auto;
}

.chart-section {
  margin-bottom: 40px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  padding: 25px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.chart-section:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
}

.chart-content {
  width: 100%;
  height: 450px;
}

.data-table-section {
  margin-top: 40px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  padding: 25px;
}

.data-table {
  width: 100%;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
  font-size: 14px;
  border-radius: 8px;
}

th, td {
  padding: 14px 16px;
  text-align: center;
  border: 1px solid #eaeef2;
}

th {
  background-color: #f8fafd;
  font-weight: 600;
  color: #2c3e50;
  position: sticky;
  top: 0;
}

tr:nth-child(even) {
  background-color: #fbfdff;
}

tr:hover {
  background-color: #f5f9ff;
}

@media (max-width: 1024px) {
  .chart-content {
    height: 400px;
  }
}

@media (max-width: 768px) {
  .chart-controls {
    flex-direction: column;
    align-items: flex-start;
    gap: 15px;
  }
  
  .chart-content {
    height: 380px;
  }
  
  th, td {
    padding: 10px 12px;
    font-size: 13px;
  }
  
  h2 {
    font-size: 22px;
  }
  
  h3 {
    font-size: 18px;
  }
}

@media (max-width: 480px) {
  .chart-content {
    height: 320px;
  }
  
  th, td {
    padding: 8px 10px;
    font-size: 12px;
  }
  
  h2 {
    font-size: 20px;
  }
  
  .data-table-section, .chart-section {
    padding: 15px;
  }
}

</style>