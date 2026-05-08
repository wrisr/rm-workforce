<div class="title"> SCG Digital Workforce 2026 classs2</div>

<style>
  .title {
    color: #ffffff;
    font-family: SCG-Font, sans-serif;
    font-weight: bold;
    font-size: 20px;
    background-color:#041e42;
    padding: 10px;
  }
  .subtitle {
    color: #424242;
    font-family: SCG-Font, sans-serif;
    font-weight: bold;
    font-size: 24px;
    padding: 24px;
  }
</style>
---

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>

<div class="subtitle">
  DO Workforce Graph test interactmode11 :
  <canvas id="workforceChartDO"></canvas>
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
    
  const workforcedo = document.getElementById('workforceChartDO');
  new Chart (workforcedo, {
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
            text: 'SCG Digital Workforce 2026'
        },
        legend: {
             position: 'bottom',
        },
        responsive: true,
        scales: {
            x: [{
                stacked: true
            }],
            y: [{
                stacked: true,
                beginAtZero: true
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
              color: 'white',
              //formatter: Math.round,
              padding: 0
            }
        }
    }
});
</script>

- End Graph -
