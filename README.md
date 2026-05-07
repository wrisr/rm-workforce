# wrisr.github.io/workforce
RM Workforce

<div>
  Original Graph :
  <canvas id="myChart"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>

<script>
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
</script>

<div>
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
              datasetLabels: 'CPS!A2:A4', // Column for series names
                indexLabels: 'CPS!B1:P1',    // Row for X-axis labels
                data: 'CPS!B2:P4' 
            }
        }
    }
});
</script>

---------

<div>
  Test Workforce Graph ALL :
  <canvas id="testChartAll"></canvas>
</div>

<script>
  const testctxall = document.getElementById('testChartAll');
  new Chart (testctxall, {
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
              datasetLabels: 'Test!B2:B4,Test!B7,Test!B10,Test!B13', // Column for series names
                indexLabels: 'Test!C1:Q1',    // Row for X-axis labels
                data: 'Test!C2:Q13' 
            }
        }
    }
});
</script>

- End Graph -
