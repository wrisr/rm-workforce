<head>
  <link rel="stylesheet" href="css/style.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>
  <script src="js/chart-aic.js" type="module"></script>
  <script src="js/sidenav.js" type="text/javascript"></script>
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
        <img src="svg/menu-excel.svg" alt="background">
      </a>
    </span>
  </div>
  
  <div class="section">
    <!-- start summary -->
    <div class="chart rounded-div">
      <div class="chartheaderleft">
        AIC Key Summary
      </div>
      <div class="chartbody">
        1 <a href="index#index-resource">link to Per Resource Type</a>
        <div class="chartsubbody">
          1.1 <a href="index#index-main-avaiplan">link to Avai / Plan</a><br>
          1.2
        </div>
      </div>
      <div class="chartbody">
        - 2 <a href="index#index-dept">link to Per Department</a>
        <div class="chartsubbody">
          2.1 <a href="index#index-dept-cps">link to Per Resource Type : CPS</a><br>
          2.2 <a href="index#index-dept-pse">link to Per Resource Type : PSE</a>
        </div>
      </div>
      <div class="chartbody">
        - 3
      </div>
      <div class="chartbody">
        ...
      </div>
    </div>
    <!-- end summary -->
    <div class="chart rounded-div" id="aic-main-mth">
      <canvas id="workforceChartAIC"></canvas>
    </div>
    <div class="chart rounded-div" id="aic-main-qtr">
      <canvas id="workforceChartAICQTR"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow" id="aic-main-avaiplan">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvai"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtr"></canvas></div>
            </div>
        </div>
    </div>
  </div>
    
  <div class="section" id="aic-resource">
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

  <div class="section" id="aic-sect-ra">
    AIC AI Research & Alliance
    <div class="chart rounded-div">
      <canvas id="workforceChartAICRA"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvaiRA"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtrRA"></canvas></div>
            </div>
        </div>
    </div>
  </div>

  <div class="section" id="aic-sect-aie">
    AIC AIET AI Engineering
    <div class="chart rounded-div">
      <canvas id="workforceChartAICAIE"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvaiAIE"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtrAIE"></canvas></div>
            </div>
        </div>
    </div>
  </div>

  <div class="section" id="aic-sect-iot">
    AIC AIET IoT Engineering
    <div class="chart rounded-div">
      <canvas id="workforceChartAICIoT"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvaiIoT"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtrIoT"></canvas></div>
            </div>
        </div>
    </div>
  </div>

  <div class="section" id="aic-sect-sai">
    AIC AIET Spatial AI Engineering
    <div class="chart rounded-div">
      <canvas id="workforceChartAICSAI"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvaiSAI"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtrSAI"></canvas></div>
            </div>
        </div>
    </div>
  </div>

  <div class="section" id="aic-sect-pi">
    AIC Product Innovation
    <div class="chart rounded-div">
      <canvas id="workforceChartAICPI"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartAICAvaiPI"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartAICPlanQtrPI"></canvas></div>
            </div>
        </div>
    </div>
  </div>
  
  <iframe src="footer.html"></iframe>
  
</body>
