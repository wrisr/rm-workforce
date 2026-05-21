<head>
  <link rel="stylesheet" href="css/style.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.14.3/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datasource@0.1.0"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/0.7.0/chartjs-plugin-datalabels.min.js"></script>
  <script src="js/chart-index.js" type="module"></script>
  <script src="js/sidenav.js" type="text/javascript"></script>
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
    <span class="subbtn">
      <a class="suburl" href="https://scgo365.sharepoint.com/:x:/r/sites/DO-ResourceManagement781-2026/_layouts/15/Doc.aspx?sourcedoc=%7BE5121AEA-3700-4875-85EF-5058B984DD9E%7D&file=DO%20Workforce%20-%20Master.xlsx&action=default&mobileredirect=true" target="_blank">
        <img src="svg/menu-excel.svg" alt="background">
      </a>
    </span>
  </div>
  
  <div class="section">
    <div class="chart rounded-div">
      <div class="chartheader">
        Executive Summary
      </div>
      <p class="chartbody">
        &#8227;&ensp;เฉลี่ย Q2 2025 – Q1 2026 <span class="text-blue">[Plan 86.10%]</span>
        <p class="chartsubbody">
          &#8226;&ensp;ปริมาณคน > ปริมาณงาน (diff average รายปี)
          <br>
          &#8226;&ensp;Top Allocation&emsp;&emsp;SD-Data 119% / SD-BA 108% / SD-SA&SRE 101%
          <br>
          &#8226;&ensp;Top Available&emsp;&emsp;&emsp;<a href="sd#sd-sect-design">SD-Design</a> 58% <span class="text-green text-italic">[Available 42%]</span> / PS-Sales 73% [Available 27%] / R&D-IoT 74% [Available 26%]
          <br>
          &#8226;&ensp;Top Diff FTE&emsp;&emsp;SE +10 FTE / SD-Design +4 FTE / PS-Sales +3 FTE	~ คนเกิน
          <br>
          &#8226;&ensp;Plan	86.48 % (Available ~ 73.74 FTE per month)
        </p>
      </p>
      <p class="chartbody">
        • Q2 2025 [Plan 95.92%]
        <p class="chartsubbody">
          • June มีปริมาณ Plan FTE สูงสุด [98.49%] เนื่องจากมีงานเข้ามาแน่นอนแล้วในช่วงปัจจุบัน ** บางโปรเจคยังไม่ start June<br>
          • ส่วนต่าง ยังเป็นตัวเลขที่สามารถจัดการได้ โดยการโยกพนักงานมาจาก Internal Project ได้<br>
          • Q2 Top Allocation	SD-CyberSec 128% / SD-BA 119% / SD-Data 119% / SD-PM 107% / SD-SA&SRE 103%	<br>
          • Q2 Top Available	SD-Design 73% [Available 27%] / R&D-IoT 86% [Available 14%] / PSI 87% [Available 13%]	<br>
          • Q2 Top Diff FTE	SE +6 FTE / SD-Design +3 FTE
        </p>
      </p>
      <p class="chartbody">
        Q1 2026 [Plan 65.05%]
        <p class="chartsubbody">
          • Available เป็นจำนวนมาก เกิดจากความไม่แน่นอนในโปรเจคใหม่ที่จะเข้ามาในปีหน้า รวมถึงมีโปรเจคที่จบตั้งแต่ปี 2025 และยังไม่มีแผนขยาย<br>
          • Top Allocation	SD-Data 109%<br>
          • Top Available	SD-Design 15% [Available 85%]<br>
          • Top Diff FTE	SE +18.83 FTE				~ คนเกิน
        </p>
      </p>
      <p class="chartbody">
        ...
      </p>
    </div>
    <div class="chart rounded-div" id="index-planactual">
      <canvas id="workforceChartDOPlanActual"></canvas>
    </div>
    <div class="chart rounded-div" id="index-main-mth">
      <canvas id="workforceChartDO"></canvas>
    </div>
    <div class="chart rounded-div" id="index-main-qtr">
      <canvas id="workforceChartDOQTR"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow" id="index-main-avaiplan">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartDOAvai"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartDOPlanQtr"></canvas></div>
            </div>
        </div>
    </div>
  </div>
    
  <div class="section" id="index-resource">
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
  
  <div class="section" id="index-dept">
    Per Department
    <div class="secwrapper">
        <div class="secrow" id="index-dept-cps">
            <div class="secleft">
              <a href="cps"><div class="chart rounded-div"><canvas id="workforceChartCPSQTR"></canvas></div></a>
            </div>
            <div class="secright">
              <a href="cps"><div class="chart rounded-div"><canvas id="workforceChartCPSPlanQtr"></canvas></div></a>
            </div>
        </div>
        <div class="secrow" id="index-dept-pse">
            <div class="secleft">
              <a href="pse"><div class="chart rounded-div"><canvas id="workforceChartPSEQTR"></canvas></div></a>
            </div>
            <div class="secright">
              <a href="pse"><div class="chart rounded-div"><canvas id="workforceChartPSEPlanQtr"></canvas></div></a>
            </div>
        </div>
        <div class="secrow" id="index-dept-sd">
            <div class="secleft">
              <a href="sd"><div class="chart rounded-div"><canvas id="workforceChartSDQTR"></canvas></div></a>
            </div>
            <div class="secright">
              <a href="sd"><div class="chart rounded-div"><canvas id="workforceChartSDPlanQtr"></canvas></div></a>
            </div>
        </div>
        <div class="secrow" id="index-dept-aic">
            <div class="secleft">
              <a href="aic"><div class="chart rounded-div"><canvas id="workforceChartAICQTR"></canvas></div></a>
            </div>
            <div class="secright">
              <a href="aic"><div class="chart rounded-div"><canvas id="workforceChartAICPlanQtr"></canvas></div></a>
            </div>
        </div>
        <div class="secrow" id="index-dept-tde">
            <div class="secleft">
              <a href="tde"><div class="chart rounded-div"><canvas id="workforceChartTDEQTR"></canvas></div></a>
            </div>
            <div class="secright">
              <a href="tde"><div class="chart rounded-div"><canvas id="workforceChartTDEPlanQtr"></canvas></div></a>
            </div>
        </div>
    </div>
  </div>
    
  <div class="section" id="index-product">
    DO Product
    <div class="chart rounded-div">
      <canvas id="workforceChartProduct"></canvas>
    </div>
  </div>
    
  <div class="section" id="index-project-top">
    Top 5 Project
    <div class="chart rounded-div">
      <canvas id="workforceChartProjectPerTeam"></canvas>
    </div>
  </div>
  
  <div class="section" id="index-revenue">
    Project Revenue
    <div class="chart rounded-div">
      <canvas id="workforceChartProjectRevenue"></canvas>
    </div>
    <div class="secwrapper">
        <div class="secrow" id="index-revenue-pspd">
            <div class="secleft">
              <div class="chart rounded-div"><canvas id="workforceChartProjectRevenuePS"></canvas></div>
            </div>
            <div class="secright">
              <div class="chart rounded-div"><canvas id="workforceChartProjectRevenuePD"></canvas></div>
            </div>
        </div>
    </div>
  </div>
  
  <iframe src="footer.html"></iframe>

</body>

