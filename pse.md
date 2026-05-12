<head>
  <link rel="stylesheet" href="style.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>
  <script>
    function openNav() {
      document.getElementById("mainSidenav").style.width = "250px";
    }
    function closeNav() {
      document.getElementById("mainSidenav").style.width = "0";
    }
  </script>
</head>

<body class="body-main">

<div id="mainSidenav" class="sidenav">
  <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>
  <a href="index">SCG Digital</a>
  <a href="cps">Commercial Products & Solutions</a>
  <a href="pse" id="selected">Platform & Software Engineering</a>
  <a href="sd">Solution Delivery</a>
  <a href="aic">AI Innovation Center</a>
  <a href="tde">Talent & Digital Enablement</a>
</div>

<div class="subtitle">
  <span class="submenu" onclick="openNav()"><span style="font-size:30px;">&#9776;</span> PSE Workforce </span>
  <a class="suburl" href="https://scgo365.sharepoint.com/:x:/r/sites/DO-ResourceManagement781-2026/_layouts/15/Doc.aspx?sourcedoc=%7B4B6DF829-33EE-4F99-B98C-71595D5368C1%7D&file=DO%20Workforce%20-%203%20PSE.xlsx&action=default&mobileredirect=true" target="_blank"><span class="subbtn">Working Sheet</span></a>
</div>

<div class="section">
  <div class="chart rounded-div">
    <canvas id="workforceChartPSE"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartPSEQTR"></canvas>
  </div>
</div>
  
<div class="section">
  Per Resource Type
  <div class="chart rounded-div">
    <canvas id="workforceChartPSEPR"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartPSECT"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartPSEOS"></canvas>
  </div>
</div>

<div class="section">
  Per Section
  <div class="chart rounded-div">
    <canvas id="workforceChartPSEPE"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartPSESE"></canvas>
  </div>
</div>

<script>

  Chart.defaults.global.defaultFontColor = '#0000008A';
  Chart.defaults.global.defaultFontFamily = "'MindSans', sans-serif";
  Chart.defaults.global.defaultFontSize = 10;

  const actions = [
  {
    name: 'Mode: index',
    handler(chart) {
      chart.options.interaction.axis = 'xy';
      chart.options.interaction.mode = 'index';
      chart.update();
    }
  }];

/*
/* MONTH
*/
    
  const ctx = document.getElementById('workforceChartPSE');
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
            pointRadius: 0,
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
            text: 'Platform & Software Engineering Workforce 2026',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            }
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A2:A7',
                indexLabels: 'GraphPSE!B1:P1',
                data: 'GraphPSE!B2:P7' 
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
              padding: 0
            }
        }
    }
});

/*
/* QUARTER
*/

const ctxqtr = document.getElementById('workforceChartPSEQTR');
  new Chart (ctxqtr, {
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
            pointRadius: 0,
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
            text: 'PSE Workforce 2026 per Quarter',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            }
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A42:A47',
                indexLabels: 'GraphPSE!B41:F41',
                data: 'GraphPSE!B42:F47' 
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
              padding: 0
            }
        }
    }
});

/*
/* PAYROLL
*/
const ctxpr = document.getElementById('workforceChartPSEPR');
  new Chart (ctxpr, {
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
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 3,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'PSE Payroll',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            },
            yAxes: [{ ticks: { beginAtZero: true } }]
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A12:A14',
                indexLabels: 'GraphPSE!B11:P11',
                data: 'GraphPSE!B12:P14' 
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
              padding: 0
            }
        }
    }
});

/*
/* CONTRACTOR
*/
const ctxct = document.getElementById('workforceChartPSECT');
  new Chart (ctxct, {
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
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 3,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'PSE Contractor',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            },
            yAxes: [{ ticks: { beginAtZero: true } }]
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A22:A24',
                indexLabels: 'GraphPSE!B21:P21',
                data: 'GraphPSE!B22:P24' 
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
              padding: 0
            }
        }
    }
});

/*
/* OUTSOURCE
*/
const ctxos = document.getElementById('workforceChartPSEOS');
  new Chart (ctxos, {
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
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 3,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'PSE Outsource',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            },
            yAxes: [{ ticks: { beginAtZero: true } }]
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A32:A34',
                indexLabels: 'GraphPSE!B31:P31',
                data: 'GraphPSE!B32:P34' 
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
              padding: 0
            }
        }
    }
});

/*
/* PSE : Platform Engineering
*/
const ctxpe = document.getElementById('workforceChartPSEPE');
  new Chart (ctxpe, {
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
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 2,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'PSE : Platform Engineering',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            },
            yAxes: [{ ticks: { beginAtZero: true } }]
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A52:A53',
                indexLabels: 'GraphPSE!B51:P51',
                data: 'GraphPSE!B52:P53' 
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
              padding: 0
            }
        }
    }
});

/*
/* PSE : Software Engineering
*/
const ctxse = document.getElementById('workforceChartPSESE');
  new Chart (ctxse, {
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
            order: 2,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 2,
            borderColor: 'rgba(237, 125, 50)',
            backgroundColor: 'rgba(237, 125, 50)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        }
    ]},
    plugins: [ChartDataSource],
    options: {
        title: {
            display: true,
            fontSize: 20,
            text: 'PSE : Software Engineering',
            padding: 20,
            fontColor: '#616161',
        },
        legend: {
            position: 'bottom',
            labels: {
              usePointStyle: true
            }
        },
        tooltips: {
          mode: 'index',
          intersect: false,
          titleFontSize: 12,
          position: 'nearest'
        },
        responsive: true,
        scales: {
            x: {
                stacked: true
            },
            y: {
                stacked: true,
                beginAtZero: true
            },
            yAxes: [{ ticks: { beginAtZero: true } }]
        },
        plugins: {
            datasource: {
                url: 'workforceresult.xlsx',
                type: 'sheet',  
                //rowMapping: 'dataset',
                datasetLabels: 'GraphPSE!A62:A63',
                indexLabels: 'GraphPSE!B61:P61',
                data: 'GraphPSE!B62:P63' 
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
              padding: 0
            }
        }
    }
});
  
</script>

</body>
