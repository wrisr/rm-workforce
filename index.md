<head>
  <link rel="stylesheet" href="style.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>
</head>

<body class="body-main">
  
<div class="subtitle">
  DO Workforce
  <div class="chart rounded-div">
    <canvas id="workforceChartDO"></canvas>
  </div>
</div>

<script>

  const actions = [
  {
    name: 'Mode: index',
    handler(chart) {
      chart.options.interaction.axis = 'xy';
      chart.options.interaction.mode = 'index';
      chart.update();
    }
  }];
    
  const ctx = document.getElementById('workforceChartDO');
  new Chart (ctx, {
    type: 'bar',
    displayColors: true,
    interaction: {
        mode: 'index',
        intersect: false
    },
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(68, 114, 196)',
            backgroundColor: 'rgba(68, 114, 196)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 3,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }, {
            borderColor: 'rgba(165, 165, 165)',
            borderWidth: 2,
            borderRadius: 10,
            //borderSkipped: false,
            backgroundColor: 'rgba(165, 165, 165)',
            order: 4,
            stack: 'groupplan'
        }, {
            backgroundColor: 'rgba(255, 191, 0)',
            order: 4,
            stack: 'groupplan'
        }, {
            backgroundColor: 'rgba(91, 155, 213)',
            order: 4,
            stack: 'groupplan'
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'SCG Digital Workforce 2026 w',
            fontFamily: "MindSans"
        },
        legend: {
            position: 'bottom',
            labels: {
              fontFamily: "'MindSans', sans-serif",
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontFamily: "'MindSans', sans-serif",
          bodyFontFamily: "'MindSans', sans-serif",
          bodyFontSize: 10
        },
        responsive: true,
        scales: {
            x: [{
                stacked: true,
                ticks: { fontFamily: "'MindSans', sans-serif", fontColor: 'blue', fontSize: 10 }
            }],
            y: [{
                stacked: true,
                beginAtZero: true,
                ticks: { fontFamily: "'MindSans', sans-serif", fontColor: 'red', fontSize: 10 }
            }]
        },
        plugins: {
            datasource: {
                url: 'testresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphAll!A2:A7',
                indexLabels: 'GraphAll!B1:P1',
                data: 'GraphAll!B2:P7' 
            },
            datalabels: {
                formatter: (value, ctx) => {
                  return;
                },
              backgroundColor: function(context) {
                return context.dataset.backgroundColor;
              },
              borderRadius: 4,
              //formatter: Math.round,
              color: 'white',
              font: {
                family: "'MindSans', sans-serif", // Set font family
                size: 10,
                weight: 'normal'
              },
              padding: 0
            }
        }
    }
});
</script>

</body>
