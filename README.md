# wrisr.github.io/workforce
RM Workforce

<div>
  Graph A :
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
  Graph New :
  <canvas id="testChart"></canvas>
</div>

<script>
  const testctx2 = document.getElementById('testChart');
  new Chart (testctx2, {
    type: 'line',
    data: {
        datasets: [{
            borderWidth: 6,
            borderColor: 'rgba(146, 242, 42, 0.85)',
            fill: false
        }, {
            borderWidth: 6,
            borderColor: 'rgba(207, 0, 15, 0.85)',
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
            yAxes: [{
                ticks: {
                    max: 160,
                    min: 0,
                }
            }]
        },
        plugins: {
            datasource: {
                url: 'testresult.xlsx'
            }
        }
    }
});
</script>

- End Graph -
