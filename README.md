# SCG Digital Workforce 2026
---

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>


<!-- div>
  Original Graph :
  <canvas id="myChart"></canvas>
</div -->

<!-- script>
  const ctx = document.getElementById('myChart');
  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
      datasets: [{
        label: '# of Votes',
        data: [12, 19, 3, 5, 2, 3],
        borderWidth: 1
      }]
    },
    options: {
      scales: {
        y: {
          beginAtZero: true
        }
      }
    }
  });
</script -->

<!-- <div>
  Test Workforce Graph CPS1 :
  <canvas id="testChart"></canvas>
</div>

<script>
  const testctx2 = document.getElementById('testChart');
  new Chart (testctx2, {
    type: 'line',
    data: {
        datasets: [{
            borderWidth: 2,
            borderColor: 'blue',
            fill: false
        }, {
            borderWidth: 2,
            borderColor: 'black',
            fill: false
        }, {
            borderWidth: 2,
            borderColor: 'orange',
            fill: false
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'SCG Digital Workforce 2026'
        },
        scales: {
            y: {
              beginAtZero: true
            }
        },
        plugins: {
            datasource: {
              url: 'testresult.xlsx',
              type: 'sheet',  
              rowMapping: 'dataset',
              datasetLabels: 'CPS!A2:A4',
                indexLabels: 'CPS!B1:P1',
                data: 'CPS!B2:P4' 
            }
        }
    }
});
</script>

---------

<div>
  Test Workforce Graph ALL 1 :
  <canvas id="testChartAll"></canvas>
</div>

<script>
  const testctxall = document.getElementById('testChartAll');
  new Chart (testctxall, {
    type: 'bar',
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 2,
            borderColor: 'red'
        }, {
            type: 'line',
            borderWidth: 1,
            borderColor: 'green',
            fill: false
        }, {
            type: 'line',
            borderWidth: 2,
            borderColor: 'blue',
            fill: false
        }, {
            backgroundColor: 'yellow',
          order: 3
        }, {
            backgroundColor: 'orange',
          order: 2
        }, {
            backgroundColor: 'grey',
          order: 1
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'SCG Digital Workforce 2026'
        },
        responsive: true,
        scales: {
            xAxes: { stacked: true },
            yAxes: {
              stacked: true,
              beginAtZero: true
            },
        },
        plugins: {
            datasource: {
              url: 'testresult.xlsx',
              type: 'sheet',  
              rowMapping: 'dataset',
              datasetLabels: 'GraphAll!A2:A7', // Column for series names
                indexLabels: 'GraphAll!B1:P1',    // Row for X-axis labels
                data: 'GraphAll!B2:P7' 
            }
        }
    }
});
</script>

---------  -->

<div>
  DO Workforce Graph test interactmode :
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
            fill: false,
            order: 1
        },{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 3
        }, {
            //borderColor: 'rgba(165, 165, 165)',
            //borderWidth: 2,
            //borderRadius: 10,
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
            tooltips: {
                mode: 'label'
            }
        }
    }
});
</script>

- End Graph -
