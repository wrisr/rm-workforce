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
  <a href="index" id="selected">SCG Digital</a>
  <a href="cps">Commercial Products & Solutions</a>
  <a href="pse">Platform & Software Engineering</a>
  <a href="sd">Solution Delivery</a>
  <a href="aic">AI Innovation Center</a>
  <a href="tde">Talent & Digital Enablement</a>
</div>

<div class="subtitle">
  <span class="submenu" onclick="openNav()"><span style="font-size:30px;">&#9776;</span> DO Workforce </span>
  <!-- a class="suburl" href="https://scgo365.sharepoint.com/:x:/r/sites/DO-ResourceManagement781-2026/_layouts/15/Doc.aspx?sourcedoc=%7BE5121AEA-3700-4875-85EF-5058B984DD9E%7D&file=DO%20Workforce%20-%20Master.xlsx&action=default&mobileredirect=true" target="_blank"><span class="subbtn">Working Sheet</span></a -->
  <span class="subbtn"><img src="menu-excel.svg" alt="test" style="position: absolute; height: 100%; width: 100%; inset: 0px; color: transparent;"></span>
</div>

<div class="section">
  <div class="chart rounded-div">
    <canvas id="workforceChartDO"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartDOQTR"></canvas>
  </div>
</div>
  
<div class="section">
  Per Resource Type
  <div class="chart rounded-div">
    <canvas id="workforceChartDOPR"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartDOCT"></canvas>
  </div>
  <div class="chart rounded-div">
    <canvas id="workforceChartDOOS"></canvas>
  </div>
  
</div>

<div class="section">
  Per Department
  <div class="secwrapper">
      <div class="secrow">
          <div class="secleft">
            <a href="cps"><div class="chart rounded-div"><canvas id="workforceChartCPSQTR"></canvas></div></a>
          </div>
          <div class="secright">
            <a href="pse"><div class="chart rounded-div"><canvas id="workforceChartPSEQTR"></canvas></div></a>
          </div>
      </div>
      <div class="secrow">
          <div class="secleft">
            <a href="sd"><div class="chart rounded-div"><canvas id="workforceChartSDQTR"></canvas></div></a>
          </div>
          <div class="secright">
            <a href="aic"><div class="chart rounded-div"><canvas id="workforceChartAICQTR"></canvas></div></a>
          </div>
      </div>
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
            text: 'SCG Digital Workforce 2026',
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
              padding: 0
            }
        }
    }
});

/*
/* QUARTER
*/

const ctxqtr = document.getElementById('workforceChartDOQTR');
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
            text: 'Workforce 2026 per Quarter',
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
                datasetLabels: 'GraphAll!A42:A47',
                indexLabels: 'GraphAll!B41:F41',
                data: 'GraphAll!B42:F47' 
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

const ctxpr = document.getElementById('workforceChartDOPR');
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
            text: 'Payroll',
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
                datasetLabels: 'GraphAll!A12:A14',
                indexLabels: 'GraphAll!B11:P11',
                data: 'GraphAll!B12:P14' 
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

const ctxct = document.getElementById('workforceChartDOCT');
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
            text: 'Contractor',
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
                datasetLabels: 'GraphAll!A22:A24',
                indexLabels: 'GraphAll!B21:P21',
                data: 'GraphAll!B22:P24' 
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

const ctxos = document.getElementById('workforceChartDOOS');
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
            text: 'Outsource',
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
                datasetLabels: 'GraphAll!A32:A34',
                indexLabels: 'GraphAll!B31:P31',
                data: 'GraphAll!B32:P34' 
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
/* QUARTER : CPS
*/

const ctxqtrcps = document.getElementById('workforceChartCPSQTR');
  new Chart (ctxqtrcps, {
    type: 'bar',
    displayColors: true,
    interaction: {
        mode: 'index',
        intersect: false
    },
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            backgroundColor: 'rgba(68, 114, 196)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 0.5,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2,
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 1,
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
            fontSize: 14,
            text: 'CPS',
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
          titleFontSize: 10,
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
                datasetLabels: 'GraphCPS!A42:A47',
                indexLabels: 'GraphCPS!B41:F41',
                data: 'GraphCPS!B42:F47' 
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
/* QUARTER : PSE
*/
const ctxqtrpse = document.getElementById('workforceChartPSEQTR');
  new Chart (ctxqtrpse, {
    type: 'bar',
    displayColors: true,
    interaction: {
        mode: 'index',
        intersect: false
    },
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            backgroundColor: 'rgba(68, 114, 196)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 0.5,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2,
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 1,
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
            fontSize: 14,
            text: 'PSE',
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
          titleFontSize: 10,
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
/* QUARTER : SD
*/
const ctxqtrsd = document.getElementById('workforceChartSDQTR');
  new Chart (ctxqtrsd, {
    type: 'bar',
    displayColors: true,
    interaction: {
        mode: 'index',
        intersect: false
    },
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            backgroundColor: 'rgba(68, 114, 196)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 0.5,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2,
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 1,
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
            fontSize: 14,
            text: 'SD',
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
          titleFontSize: 10,
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
                datasetLabels: 'GraphSD!A42:A47',
                indexLabels: 'GraphSD!B41:F41',
                data: 'GraphSD!B42:F47' 
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
/* QUARTER : AIC
*/
const ctxqtraic = document.getElementById('workforceChartAICQTR');
  new Chart (ctxqtraic, {
    type: 'bar',
    displayColors: true,
    interaction: {
        mode: 'index',
        intersect: false
    },
    data: {
        datasets: [{
            type: 'line',
            borderWidth: 1,
            borderColor: 'rgba(68, 114, 196)',
            backgroundColor: 'rgba(68, 114, 196)',
            fill: false,
            order: 1,
            datalabels: {align: 'end', anchor: 'end', padding: 4}
        },{
            type: 'line',
            borderWidth: 0.5,
            borderColor: 'rgba(68, 114, 196)',
            borderDash: [5, 5],
            fill: false,
            order: 2,
            pointRadius: 0,
            datalabels: {display: false}
        },{
            type: 'line',
            borderWidth: 1,
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
            fontSize: 14,
            text: 'AIC',
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
          titleFontSize: 10,
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

</script>

</body>
