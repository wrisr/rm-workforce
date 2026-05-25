<head>
  <link rel="stylesheet" href="css/style.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>
  <script src="js/chart-cps.js" type="module"></script>
  <script src="js/sidenav.js" type="text/javascript"></script>
</head>

<body class="body-main">

  <div id="mainSidenav" class="sidenav">
    <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>
    <a href="index">SCG Digital</a>
    <a href="cps" id="selected">Commercial Products & Solutions</a>
    <a href="pse">Platform & Software Engineering</a>
    <a href="sd">Solution Delivery</a>
    <a href="aic">AI Innovation Center</a>
    <a href="tde">Talent & Digital Enablement</a>
  </div>
  
  <div class="subtitle">
    <span class="submenu" onclick="openNav()"><span style="font-size:30px;">&#9776;</span> CPS Workforce </span>
    <span class="subbtn">
      <a class="suburl" href="https://scgo365.sharepoint.com/:x:/r/sites/DO-ResourceManagement781-2026/_layouts/15/Doc.aspx?sourcedoc=%7B9BBF68FA-8ED4-4047-B96B-FBAB880F6546%7D&file=DO%20Workforce%20-%202%20CPS.xlsx&action=default&mobileredirect=true" target="_blank">
        <img src="svg/menu-excel.svg" alt="background">
      </a>
    </span>
  </div>
  
  <div class="section">
    <!-- start summary -->
    <div class="chart rounded-div">
      <div class="chartheader">
        Executive Summary
      </div>
      <div class="chartbody">
        &#8227;&ensp;Q2 2026 – Q1 2027 <span class="text-plan">[Plan 81.59%]</span>
      </div>
      <div class="chartsubbody">
        <div class="chartsubbodycontainer">
          &#8226;&ensp;ปริมาณคน > ปริมาณงาน (diff average รายปี)
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Allocation</div>
          <div class="chartsubbodydata">
            <a href="sd#sd-sect-qa">SD-QA</a> 106.10%<br>
            <a href="sd#sd-sect-sre">SD-SRE</a> 105.46%<br>
            <a href="sd#sd-sect-tm">SD-TM</a> 103.52%
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Available</div>
          <div class="chartsubbodydata">
            <a href="aic#aic-sect-sai">AIC-SAI</a> 58.92% <span class="text-avai">[Available 41.08%]</span><br>
            <a href="aic#aic-sect-aie">AIC-AIE</a> 62.62% <span class="text-avai">[Available 37.38%]</span><br>
            <a href="aic#aic-sect-iot">AIC-IoT</a> 67.62% <span class="text-avai">[Available 32.38%]</span><br>
            <a href="sd#sd-sect-design">SD-Design</a> 67.89% <span class="text-avai">[Available 32.11%]</span> 
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Diff FTE</div>
          <div class="chartsubbodydata">
            <a href="pse#pse-sect-se">PSE-SE</a> <span class="text-avai">+7.2 FTE</span><br>
            <a href="aic#aic-sect-aie">AIC-AIE</a> <span class="text-avai">+3 FTE</span><br>
            <a href="aic#aic-sect-iot">AIE-IoT</a> <span class="text-avai">+1.7 FTE</span><br> 
            <a href="sd#sd-sect-data">SD-Data</a> <span class="text-avai">+1.7 FTE</span>
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Average Plan</div>
          <div class="chartsubbodydata">
            81.59 % (Available ~ <span class="text-avai">+27.68 FTE</span> per month)
          </div>
        </div>
      </div>
      <div class="chartbody">
        &#8227;&ensp;Q2 2026 <span class="text-plan">[Plan 91.08%]</span>
      </div>
      <div class="chartsubbody">
        <div class="chartsubbodycontainer">
        &#8226;&ensp;May มีปริมาณ Plan FTE สูงสุด [92.03%] เนื่องจากมีงานเข้ามาแน่นอนแล้วในช่วงปัจจุบัน
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Allocation</div>
          <div class="chartsubbodydata">
            <a href="sd#sd-sect-sre">SD-SRE</a> 130.08%<br>
            <a href="sd#sd-sect-qa">SD-QA</a> 105.79%<br>
            <a href="sd#sd-sect-ba">SD-BA</a> 104.75%<br>
            <a href="cps#cps-sect-bd">CPS-BD</a> 103.94%
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Available</div>
          <div class="chartsubbodydata">
            <a href="sd#sd-sect-tm">SD-TM</a> 78.08% <span class="text-avai">[Available 21.92%]</span><br>
            <a href="aic#aic-sect-sai">AIC-SAI</a> 81.92% <span class="text-avai">[Available 18.08%]</span><br> 
            <a href="aic#aic-sect-iot">AIC-IoT</a> 85.00% <span class="text-avai">[Available 15.00%]</span> 
          </div>
        </div>
          <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Diff FTE</div>
          <div class="chartsubbodydata">
            <a href="pse#pse-sect-se">PSE-SE</a> <span class="text-avai">+2.6 FTE</span><br>
            <a href="aic#aic-sect-aie">AIC-AIE</a> <span class="text-avai">+0.97 FTE</span><br> 
            <a href="sd#sd-sect-data">SD-Data</a> <span class="text-avai">+0.92 FTE</span><br>
            <a href="aic#aic-sect-iot">AIC-IoT</a> <span class="text-avai">+0.9 FTE</span> 
          </div>
        </div>
        <div class="chartsubbodycontainer">
          &#8226;&ensp;ยังเป็นตัวเลขที่สามารถจัดการได้ โดยทีมที่พนักงานเกิน (PSE-SE) สามารถโยกมาทำ Internal Project ได้
        </div>
        <div class="chartsubbodycontainer">
          &#8226;&ensp;ส่วนทีมที่พนักงานขาด (SD-SRE) กำลังอยู่ในช่วงการสรรหาพนักงานใหม่มาเพิ่มเติม
        </div>
      </div>
      <div class="chartbody">
        &#8227;&ensp;Q1 2027 <span class="text-plan">[Plan 64.30%]</span>
      </div>
      <div class="chartsubbody">
        <div class="chartsubbodycontainer">
          &#8226;&ensp;Available เป็นจำนวนมาก เกิดจากความไม่แน่นอนในโปรเจคใหม่ที่จะเข้ามาในปีหน้า รวมถึงมีโปรเจคที่จบตั้งแต่ปี 2026 และยังไม่มีแผนขยาย
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Allocation</div>
          <div class="chartsubbodydata">
            <a href="sd#sd-sect-tm">SD-TM</a> 130%
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Available</div>
          <div class="chartsubbodydata">
            <a href="aic#aic-sect-sai">AIC-SAI</a> 10% <span class="text-avai">[Available 90%]</span><br>
            <a href="sd#sd-sect-pm">SD-PM</a> 25% <span class="text-avai">[Available 75%]</span><br>
            <a href="sd#sd-sect-design">SD-Design</a> 27.86% <span class="text-avai">[Available 72.14%]</span><br>
            <a href="aic#aic-sect-iot">AIC-IoT</a> 28% <span class="text-avai">[Available 72%]</span> 
          </div>
        </div>
        <div class="chartsubbodycontainer">
          <div class="chartsubbodytitle">&#8226;&ensp;Top Diff FTE</div>
          <div class="chartsubbodydata">
            <a href="pse#pse-sect-se">PSE-SE</a> <span class="text-avai"> +16.35 FTE</span>
          </div>
        </div>
      </div>
    </div>
    <!-- end summary -->
    <div class="chart rounded-div" id="cps-main-mth">
      <canvas id="workforceChartCPS"></canvas>
    </div>
    <div class="chart rounded-div" id="cps-main-qtr">
      <canvas id="workforceChartCPSQTR"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow" id="cps-main-avaiplan">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartCPSAvai"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartCPSPlanQtr"></canvas></div>
            </div>
        </div>
    </div>
  </div>
    
  <div class="section" id="cps-resource">
    Per Resource Type
    <div class="chart rounded-div">
      <canvas id="workforceChartCPSPR"></canvas>
    </div>
    <div class="chart rounded-div">
      <canvas id="workforceChartCPSCT"></canvas>
    </div>
    <div class="chart rounded-div">
      <canvas id="workforceChartCPSOS"></canvas>
    </div>
  </div>

  <div class="section" id="cps-sect-bd">
    CPS Business Development & Partnerships
    <div class="chart rounded-div">
      <canvas id="workforceChartCPSBD"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartCPSAvaiBD"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartCPSPlanQtrBD"></canvas></div>
            </div>
        </div>
    </div>
  </div>

  <div class="section" id="cps-sect-po">
    CPS Product Commercialization
    <div class="chart rounded-div">
      <canvas id="workforceChartCPSPO"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartCPSAvaiPO"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartCPSPlanQtrPO"></canvas></div>
            </div>
        </div>
    </div>
  </div>
  
  <iframe src="footer.html"></iframe>

</body>
