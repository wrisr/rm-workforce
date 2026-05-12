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
  <a href="pse">Platform & Software Engineering</a>
  <a href="sd">Solution Delivery</a>
  <a href="aic" id="selected">AI Innovation Center</a>
  <a href="tde">Talent & Digital Enablement</a>
</div>

<div class="subtitle">
  <span class="submenu" onclick="openNav()"><span style="font-size:30px;">&#9776;</span> AIC Workforce </span>
  <span class="subbtn">
    <a class="suburl" href="https://scgo365.sharepoint.com/:x:/r/sites/DO-ResourceManagement781-2026/_layouts/15/Doc.aspx?sourcedoc=%7BD68329D4-3D1A-4AEA-BD0D-DD0EF3E5B83E%7D&file=DO%20Workforce%20-%205%20AIC.xlsx&action=default&mobileredirect=true" target="_blank">
      <img src="menu-excel.svg" alt="background">
    </a>
  </span>
</div>

<div class="section">
  <div class="chart rounded-div">
    <canvas id="workforceChartAIC"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICQTR"></canvas>
  </div>
</div>
  
<div class="section">
  Per Resource Type
  <div class="chart rounded-div">
    <canvas id="workforceChartAICPR"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICCT"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICOS"></canvas>
  </div>
</div>

<div class="section">
  Per Section
  <div class="chart rounded-div">
    <canvas id="workforceChartAICRA"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICAIE"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICIoT"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICSAI"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartAICPI"></canvas>
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
    
  const ctx = document.getElementById('workforceChartAIC');
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
            text: 'AI Innovation Center Workforce 2026',
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
                datasetLabels: 'GraphAIC!A2:A7',
                indexLabels: 'GraphAIC!B1:P1',
                data: 'GraphAIC!B2:P7' 
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

const ctxqtr = document.getElementById('workforceChartAICQTR');
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
            text: 'AIC Workforce 2026 per Quarter',
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
                datasetLabels: 'GraphAIC!A42:A47',
                indexLabels: 'GraphAIC!B41:F41',
                data: 'GraphAIC!B42:F47' 
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
const ctxpr = document.getElementById('workforceChartAICPR');
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
            text: 'AIC Payroll',
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
                datasetLabels: 'GraphAIC!A12:A14',
                indexLabels: 'GraphAIC!B11:P11',
                data: 'GraphAIC!B12:P14' 
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
const ctxct = document.getElementById('workforceChartAICCT');
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
            text: 'AIC Contractor',
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
                datasetLabels: 'GraphAIC!A22:A24',
                indexLabels: 'GraphAIC!B21:P21',
                data: 'GraphAIC!B22:P24' 
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
const ctxos = document.getElementById('workforceChartAICOS');
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
            text: 'AIC Outsource',
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
                datasetLabels: 'GraphAIC!A32:A34',
                indexLabels: 'GraphAIC!B31:P31',
                data: 'GraphAIC!B32:P34' 
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
/* 1 - AIC : AI Research & Alliance
*/
const ctxra = document.getElementById('workforceChartAICRA');
  new Chart (ctxra, {
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
            text: 'AIC : AI Research & Alliance',
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
                datasetLabels: 'GraphAIC!A52:A53',
                indexLabels: 'GraphAIC!B51:P51',
                data: 'GraphAIC!B52:P53' 
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
/* 2 - AIC : AIET AI Engineering
*/
const ctxaie = document.getElementById('workforceChartAICAIE');
  new Chart (ctxaie, {
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
            text: 'AIC : AIET AI Engineering',
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
                datasetLabels: 'GraphAIC!A62:A63',
                indexLabels: 'GraphAIC!B61:P61',
                data: 'GraphAIC!B62:P63' 
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
/* 3 - AIC : AIET IoT Engineering
*/
const ctxiot = document.getElementById('workforceChartAICIoT');
  new Chart (ctxiot, {
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
            text: 'AIC : AIET IoT Engineering',
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
                datasetLabels: 'GraphAIC!A72:A73',
                indexLabels: 'GraphAIC!B71:P71',
                data: 'GraphAIC!B72:P73' 
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
/* 4 - AIC : AIET Spatial AI Engineering
*/
const ctxsai = document.getElementById('workforceChartAICSAI');
  new Chart (ctxsai, {
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
            text: 'AIC : AIET Spatial AI Engineering',
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
                datasetLabels: 'GraphAIC!A82:A83',
                indexLabels: 'GraphAIC!B81:P81',
                data: 'GraphAIC!B82:P83' 
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
/* 5 - AIC : Product Innovation
*/
const ctxpi = document.getElementById('workforceChartAICPI');
  new Chart (ctxpi, {
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
            text: 'AIC : Product Innovation',
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
                datasetLabels: 'GraphAIC!A92:A93',
                indexLabels: 'GraphAIC!B91:P91',
                data: 'GraphAIC!B92:P93' 
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
