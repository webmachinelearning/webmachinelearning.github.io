---
layout: page
title: Implementation Status of WebNN Operations
permalink: /webnn-status/
---

<style>
.post img {
 height: 24px;
 margin: 4px 0;
 transform: none;
 display: inline-block;
 min-width: 24px;
}

.post .onnxrt img {
 width: 80px;
}

.post .tflite img {
 width: 102px;
}

.post table {
  font-size: 0.8rem;
}

.post table tr td {
  text-align: left;
}

.post table tr td:nth-child(1), 
.post table tr td:nth-child(2),
.post table tr td:nth-child(4), 
.post table tr td:nth-child(6),
.post table tr td:nth-child(8), 
.post table tr td:nth-child(10) {
  text-align: center;
}

.post table.framework tr td:nth-child(2), 
.post table.framework tr td:nth-child(4) {
  text-align: left;
}

.post table.framework tr td:nth-child(3), 
.post table.framework tr td:nth-child(5) {
  text-align: center;
}

.post table td {
  padding: 4px 4px;
  vertical-align: middle;
}

.post table th {
  padding: 4px 4px;
}

.impl_status {
   text-align: center;
   display: grid; 
   grid-template-columns: 1fr 1fr 1fr;
   gap: 0px;
   border: 1px solid #dfe2e5;
   padding: 12px;
   font-size: 0.9em;
}

.impl_status_framework {
   text-align: center;
   display: grid; 
   grid-template-columns: 1fr 1fr;
   gap: 0px;
   border: 1px solid #dfe2e5;
   padding: 12px;
   font-size: 0.9em;
}

.impl_status .title {
  font-size: 1rem;
  line-height: 1rem;
}
.post-content table th {
  font-weight: 400;
  font-size: 0.9rem;
  line-height: 0.9rem;
}

.post svg#w3 {
  transform: none;
  height: 36px;
  width: 72px;
}

sup {
  font-size: 0.7rem;
}

.impl_status .title {
  margin-bottom: 0.4rem;
}

.impl_status div {
  margin: 0 12px;
}

#cros {
  width: 6.4rem;
  height: 3.2rem;
  margin-left: 2px;
  margin-bottom: -3px;
  transform: rotateY(0deg) rotate(0deg);
}

.mt-2 {
  margin-top: 20px;
}
</style>

<table>
  <thead>
    <tr class="title">
      <th rowspan="3">
        <a href="https://www.w3.org/TR/webnn/">
          <svg id="w3" x="0px" y="0px" viewBox="0 0 357.5 287" style="enable-background:new 0 0 357.5 287;">
            <style type="text/css">
              .st0 {
                fill: #005A9C;
              }

              .st1 {
                fill: #221B0A;
              }
            </style>
            <g>
              <path class="st0" d="M118.4,76.6l24.2,82.4l24.2-82.4h17.5l-40.1,135.3h-1.7l-25.1-83.8l-25.1,83.8h-1.7L50.8,76.6h17.5L92.5,159
                    l16.4-55.5l-8-26.9L118.4,76.6L118.4,76.6z" />
              <path class="st0" d="M234.2,168.5c0,12.3-3.3,22.6-9.8,30.9c-6.5,8.3-15,12.5-25.3,12.5c-7.8,0-14.6-2.5-20.4-7.4
                    c-5.8-5-10.1-11.7-12.9-20.1l13.7-5.7c2,5.1,4.7,9.2,7.9,12.1c3.3,2.9,7.1,4.4,11.6,4.4c4.7,0,8.6-2.6,11.9-7.9
                    c3.2-5.2,4.8-11.5,4.8-18.9c0-8.1-1.7-14.4-5.2-18.9c-4-5.2-10.3-7.9-18.9-7.9h-6.7v-8l23.4-40.4h-28.2l-7.9,13.4h-5V76.6h65.1v8.2
                    l-24.7,42.6c8.7,2.8,15.3,7.9,19.7,15.2C232,149.9,234.2,158.6,234.2,168.5L234.2,168.5z" />
              <path class="st1"
                d="M302.2,75.9l2.8,17.3l-10.1,19.2c0,0-3.9-8.2-10.3-12.7c-5.4-3.8-8.9-4.6-14.4-3.5
                    c-7.1,1.5-15.1,9.9-18.6,20.3c-4.2,12.5-4.2,18.5-4.4,24c-0.2,8.9,1.2,14.1,1.2,14.1s-6.1-11.3-6-27.8c0-11.8,1.9-22.5,7.4-33.1
                    c4.8-9.3,11.9-14.9,18.3-15.5c6.6-0.7,11.7,2.5,15.7,5.9c4.2,3.6,8.5,11.4,8.5,11.4L302.2,75.9L302.2,75.9z" />
              <path class="st1" d="M303.4,173.6c0,0-4.4,7.9-7.2,11c-2.8,3.1-7.7,8.5-13.8,11.2c-6.1,2.7-9.3,3.2-15.4,2.6
                    c-6-0.6-11.7-4.1-13.6-5.5c-2-1.4-7-5.8-9.8-9.7c-2.9-4-7.3-12-7.3-12s2.5,8,4,11.4c0.9,2,3.6,8,7.5,13.2
                    c3.6,4.9,10.7,13.3,21.4,15.1c10.7,1.9,18.1-2.9,19.9-4.1c1.8-1.2,5.7-4.4,8.1-7c2.5-2.7,4.9-6.2,6.3-8.2c1-1.5,2.6-4.6,2.6-4.6
                    L303.4,173.6L303.4,173.6z" />
            </g>
          </svg>
          <br />WebNN Spec
        </a>
      </th>
      <th rowspan="3">Web Platform<br />Tests</th>
      <th colspan="6">
        Chromium Implementation
      </th>
    </tr>
    <tr class="title">
      <th colspan="2"><img src="https://wpt.fyi/static/win.svg"> <img
          src="https://wpt.fyi/static/linux.svg"><br />XNNPack · CPU
        backend
        <sup>1</sup>
      </th>
      <th colspan="2"><img src="https://wpt.fyi/static/win.svg"><br />DirectML · GPU backend <sup>2</sup>
      </th>
         <th colspan="2">
          <svg id="cros"
            width="67.775795mm"
            height="14.390643mm"
            viewBox="0 0 67.775795 14.390643"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:svg="http://www.w3.org/2000/svg">
            <sodipodi:namedview
              id="namedview1"
              pagecolor="#ffffff"
              bordercolor="#000000"
              borderopacity="0.25"
              inkscape:showpageshadow="2"
              inkscape:pageopacity="0.0"
              inkscape:pagecheckerboard="0"
              inkscape:deskcolor="#d1d1d1"
              inkscape:document-units="mm" />
            <defs
              id="defs1">
              <linearGradient
                id="a"
                x1="3.2172999"
                y1="15"
                x2="44.7812"
                y2="15"
                gradientUnits="userSpaceOnUse">
                <stop
                  offset="0"
                  stop-color="#d93025"
                  id="stop1" />
                <stop
                  offset="1"
                  stop-color="#ea4335"
                  id="stop2" />
              </linearGradient>
              <linearGradient
                id="b"
                x1="20.721901"
                y1="47.6791"
                x2="41.503899"
                y2="11.6837"
                gradientUnits="userSpaceOnUse">
                <stop
                  offset="0"
                  stop-color="#fcc934"
                  id="stop3" />
                <stop
                  offset="1"
                  stop-color="#fbbc04"
                  id="stop4" />
              </linearGradient>
              <linearGradient
                id="c"
                x1="26.598101"
                y1="46.501499"
                x2="5.8161001"
                y2="10.506"
                gradientUnits="userSpaceOnUse">
                <stop
                  offset="0"
                  stop-color="#1e8e3e"
                  id="stop5" />
                <stop
                  offset="1"
                  stop-color="#34a853"
                  id="stop6" />
              </linearGradient>
            </defs>
            <g
              inkscape:label="Livello 1"
              inkscape:groupmode="layer"
              id="layer1"
              transform="translate(-127.52917,-127.79374)">
              <path
                fill="#5f6368"
                d="m 189.71962,134.80547 a 4.0613541,4.0613541 0 0 1 -4.06136,4.06135 4.0613541,4.0613541 0 0 1 -4.06135,-4.06135 4.0613541,4.0613541 0 0 1 4.06135,-4.06136 4.0613541,4.0613541 0 0 1 4.06136,4.06136 z m -4.03408,3.12459 a 3.127375,3.0241875 89.5 0 0 2.99681,-3.15362 3.127375,3.0241875 89.5 0 0 -3.05136,-3.10086 3.127375,3.0241875 89.5 0 0 -2.99681,3.15362 3.127375,3.0241875 89.5 0 0 3.05136,3.10086 z"
                id="path9"
                inkscape:export-filename="path9.svg"
                inkscape:export-xdpi="96"
                inkscape:export-ydpi="96"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 195.30497,136.34005 v 0.61648 q -0.82814,2.46062 -3.50573,1.76212 -1.30439,-0.34131 -1.86531,-1.88648 a 0.07408333,0.07408333 0 0 1 0.0423,-0.0952 l 0.7673,-0.30427 q 0.0714,-0.0291 0.10054,0.0423 0.66939,1.64041 2.22514,1.39964 c 0.85196,-0.12964 1.44727,-0.92339 1.07421,-1.75948 -0.39423,-0.88635 -1.93939,-1.12448 -2.74637,-1.52664 -1.77007,-0.88636 -1.4949,-3.11944 0.28046,-3.67771 q 2.16429,-0.67998 3.34168,1.29117 a 0.08995833,0.09260417 62.5 0 1 -0.0423,0.12964 l -0.73819,0.33073 a 0.08202083,0.08466667 63.5 0 1 -0.10848,-0.0344 q -0.72231,-1.24618 -2.05581,-0.84402 c -0.75671,0.23019 -1.20121,1.1483 -0.50535,1.72244 0.62177,0.51329 1.49489,0.64029 2.29129,1.00013 q 1.2065,0.54768 1.44462,1.83356 z"
                id="path10"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 152.04031,133.97732 q 1.1721,-1.21708 2.61408,-0.53975 0.98425,0.45773 1.016,1.7489 0.037,1.53458 0.008,3.43958 -0.003,0.0741 -0.0741,0.0741 l -0.83079,-0.003 q -0.0661,0 -0.0688,-0.0661 -0.045,-1.39965 0.005,-2.68287 c 0.0423,-1.06098 -0.2831,-2.032 -1.59014,-1.80975 -0.80434,0.13493 -1.16946,0.94456 -1.16417,1.70127 q 0.005,1.41287 0.005,2.74637 0,0.10848 -0.11112,0.11113 l -0.7329,0.005 q -0.14023,0 -0.14023,-0.14023 v -7.52475 q 0,-0.13229 0.12965,-0.12965 l 0.75671,0.0185 q 0.11112,0.003 0.11112,0.11377 l -0.0476,2.8919 q -0.003,0.16404 0.11377,0.045 z"
                id="path11"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 147.54768,137.94342 q 1.06627,0.0503 1.56898,-0.84931 0.0741,-0.13229 0.21167,-0.0714 l 0.60854,0.26723 q 0.14023,0.0609 0.0661,0.19315 -0.85989,1.55839 -2.7305,1.34144 c -1.90764,-0.21961 -2.82575,-2.28071 -2.12725,-3.9423 0.87313,-2.07697 3.73063,-2.31775 4.84188,-0.27516 q 0.0608,0.11112 -0.0556,0.15875 l -0.67204,0.29104 a 0.15875,0.15875 0 0 1 -0.20373,-0.0741 q -0.4154,-0.8308 -1.31763,-0.87313 c -2.29394,-0.11112 -2.43946,3.72533 -0.1905,3.83381 z"
                id="path15"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 162.97363,138.88254 a 2.8495625,2.7807708 89.4 0 1 -2.81046,-2.82028 2.8495625,2.7807708 89.4 0 1 2.75077,-2.87853 2.8495625,2.7807708 89.4 0 1 2.81046,2.82027 2.8495625,2.7807708 89.4 0 1 -2.75077,2.87854 z m -0.0238,-0.9206 a 1.9314583,1.7727083 89.9 0 0 1.76935,-1.93455 1.9314583,1.7727083 89.9 0 0 -1.77607,-1.92836 1.9314583,1.7727083 89.9 0 0 -1.76935,1.93455 1.9314583,1.7727083 89.9 0 0 1.77607,1.92836 z"
                id="path16"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 167.68512,133.97997 c 0.33867,-0.28575 0.64558,-0.57415 1.09008,-0.68792 q 1.17211,-0.29633 1.92881,0.48419 a 0.69585416,0.68262499 13.8 0 1 0.15875,0.25664 q 0.0159,0.0503 0.0609,0.0847 0.10054,0.0767 0.17198,-0.0265 0.57944,-0.82021 1.54252,-0.87048 1.93939,-0.0952 2.12989,1.87061 0.082,0.83608 0.0238,3.4925 -0.003,0.11641 -0.12171,0.11641 h -0.80433 q -0.11907,0 -0.11642,-0.11906 0.0106,-1.50813 -0.005,-3.19352 c -0.0159,-1.99496 -2.45004,-1.47902 -2.49238,0.12171 q -0.0503,1.87854 -0.0238,3.05329 0.003,0.13758 -0.13494,0.13758 l -0.78316,-0.003 q -0.1323,0 -0.12965,-0.1323 0.0265,-1.4896 -0.005,-3.15647 c -0.0397,-2.02142 -2.42623,-1.49755 -2.48709,0.0661 q -0.0688,1.67746 -0.0265,3.09298 0.003,0.13494 -0.12965,0.13229 h -0.80169 a 0.1031875,0.10054167 0 0 1 -0.10318,-0.10054 l -0.003,-5.06942 q 0,-0.17991 0.17992,-0.17991 l 0.64293,0.003 q 0.17198,0.003 0.15346,0.17463 l -0.037,0.38629 q -0.0212,0.18521 0.12171,0.0662 z"
                id="path17"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 176.65714,136.39297 q 0.16669,0.96572 0.84931,1.31762 1.40494,0.72231 2.35744,-0.59531 0.0397,-0.0529 0.0979,-0.0291 l 0.70643,0.30427 q 0.0662,0.0291 0.0344,0.0952 c -0.49742,1.00013 -1.47638,1.4605 -2.59027,1.35203 -2.70669,-0.26194 -3.39196,-4.0349 -1.05304,-5.32871 0.98689,-0.54504 2.44475,-0.35984 3.19352,0.54239 q 0.71437,0.86254 0.63235,2.02142 -0.0106,0.16933 -0.18256,0.16933 l -3.91319,-0.008 q -0.15875,0 -0.13229,0.15875 z m 0.16404,-0.99748 2.96863,-0.0106 a 0.03439583,0.03439583 0 0 0 0.0344,-0.0344 v -0.0238 a 1.2012083,1.4896041 89.8 0 0 -1.49489,-1.19591 h -0.0582 a 1.2012083,1.4896041 89.8 0 0 -1.48431,1.2065 v 0.0238 a 0.03439583,0.03439583 0 0 0 0.0344,0.0344 z"
                id="path18"
                style="stroke-width:0.264583" />
              <path
                fill="#5f6368"
                d="m 158.0146,134.08051 q 0.66146,-1.06892 2.10344,-0.73554 a 0.079375,0.079375 0 0 1 0.0556,0.10847 l -0.29634,0.74348 a 0.1349375,0.1349375 0 0 1 -0.15345,0.082 c -1.15888,-0.254 -1.85473,0.57415 -1.81769,1.68805 q 0.0476,1.44462 0.003,2.63525 -0.005,0.10054 -0.10583,0.10054 l -0.79639,-0.005 a 0.1349375,0.13229166 0 0 1 -0.13494,-0.1323 v -5.08793 q 0,-0.127 0.12964,-0.127 l 0.73555,0.003 a 0.14022916,0.13758333 4.3 0 1 0.13758,0.15611 q -0.037,0.2831 0.0106,0.54768 0.0344,0.17728 0.12965,0.0238 z"
                id="path19"
                style="stroke-width:0.264583" />
              <g
                id="g19"
                transform="matrix(0.30224767,0,0,0.29980472,127.52917,127.79376)"
                style="display:inline">
                <circle
                  cx="24"
                  cy="23.994699"
                  r="12"
                  style="fill:#ffffff"
                  id="circle6" />
                <path
                  d="M 3.2154,36 A 24,24 0 1 0 12,3.2154 24,24 0 0 0 3.2154,36 Z M 34.3923,18 A 12,12 0 1 1 18,13.6077 12,12 0 0 1 34.3923,18 Z"
                  style="fill:none"
                  id="path6-1" />
                <path
                  d="M 24,12 H 44.7812 A 23.9939,23.9939 0 0 0 3.2173,12.0029 L 13.6079,30 13.6172,29.9976 A 11.9852,11.9852 0 0 1 24,12 Z"
                  style="fill:url(#a)"
                  id="path7-2" />
                <circle
                  cx="24"
                  cy="24"
                  r="9.5"
                  style="fill:#1a73e8"
                  id="circle7" />
                <path
                  d="M 34.3913,30.0029 24.0007,48 A 23.994,23.994 0 0 0 44.78,12.0031 H 23.9989 l -0.0025,0.0093 a 11.985,11.985 0 0 1 10.3949,17.9905 z"
                  style="fill:url(#b)"
                  id="path8-0" />
                <path
                  d="M 13.6086,30.0031 3.218,12.006 A 23.994,23.994 0 0 0 24.0025,48 L 34.3931,30.0029 34.3864,29.9961 a 11.9852,11.9852 0 0 1 -20.7778,0.007 z"
                  style="fill:url(#c)"
                  id="path9-4" />
              </g>
            </g>
          </svg>

         <br />MLService · CPU backend <sup>3</sup>
      </th>
    </tr>
    <tr class="title">
      <th>Operations
      </th>
      <th>
        <img src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-canary/chrome-canary_128x128.png" />
        <img
          src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge-canary/edge-canary_128x128.png" /> <sup>4</sup>
      </th>
      <th>Operations</th>
      <th>
        <img src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-canary/chrome-canary_128x128.png" />
        <img
          src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge-canary/edge-canary_128x128.png" /> <sup>5</sup>
      </th>
       <th>Operations</th>
      <th>
        <img src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-canary/chrome-canary_128x128.png" /> <sup>6</sup>
      </th>
    </tr>
  </thead>
  <tbody id="ops"></tbody>
</table>

<div class="impl_status">
    <div class="title">XNNPack/CPU backend</div>
    <div class="title">DirectML/GPU backend</div>
    <div class="title">MLServie/CPU backend</div>
    <div>
        <div>✅ Supported (<span id="x_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="x_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="x_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
    <div>
        <div>✅ Supported (<span id="dml_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="dml_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="dml_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
        <div>
        <div>✅ Supported (<span id="mlservice_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="mlservice_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="mlservice_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
</div> 

<h1 class="post-title mt-2">JavaScript ML Frameworks Integration Status</h1>

<table class="framework">
  <thead>
    <tr class="title">
      <th rowspan="3">
        <a href="https://www.w3.org/TR/webnn/">
          <svg id="w3" x="0px" y="0px" viewBox="0 0 357.5 287" style="enable-background:new 0 0 357.5 287;">
            <style type="text/css">
              .st0 {
                fill: #005A9C;
              }

              .st1 {
                fill: #221B0A;
              }
            </style>
            <g>
              <path class="st0" d="M118.4,76.6l24.2,82.4l24.2-82.4h17.5l-40.1,135.3h-1.7l-25.1-83.8l-25.1,83.8h-1.7L50.8,76.6h17.5L92.5,159
                    l16.4-55.5l-8-26.9L118.4,76.6L118.4,76.6z" />
              <path class="st0" d="M234.2,168.5c0,12.3-3.3,22.6-9.8,30.9c-6.5,8.3-15,12.5-25.3,12.5c-7.8,0-14.6-2.5-20.4-7.4
                    c-5.8-5-10.1-11.7-12.9-20.1l13.7-5.7c2,5.1,4.7,9.2,7.9,12.1c3.3,2.9,7.1,4.4,11.6,4.4c4.7,0,8.6-2.6,11.9-7.9
                    c3.2-5.2,4.8-11.5,4.8-18.9c0-8.1-1.7-14.4-5.2-18.9c-4-5.2-10.3-7.9-18.9-7.9h-6.7v-8l23.4-40.4h-28.2l-7.9,13.4h-5V76.6h65.1v8.2
                    l-24.7,42.6c8.7,2.8,15.3,7.9,19.7,15.2C232,149.9,234.2,158.6,234.2,168.5L234.2,168.5z" />
              <path class="st1"
                d="M302.2,75.9l2.8,17.3l-10.1,19.2c0,0-3.9-8.2-10.3-12.7c-5.4-3.8-8.9-4.6-14.4-3.5
                    c-7.1,1.5-15.1,9.9-18.6,20.3c-4.2,12.5-4.2,18.5-4.4,24c-0.2,8.9,1.2,14.1,1.2,14.1s-6.1-11.3-6-27.8c0-11.8,1.9-22.5,7.4-33.1
                    c4.8-9.3,11.9-14.9,18.3-15.5c6.6-0.7,11.7,2.5,15.7,5.9c4.2,3.6,8.5,11.4,8.5,11.4L302.2,75.9L302.2,75.9z" />
              <path class="st1" d="M303.4,173.6c0,0-4.4,7.9-7.2,11c-2.8,3.1-7.7,8.5-13.8,11.2c-6.1,2.7-9.3,3.2-15.4,2.6
                    c-6-0.6-11.7-4.1-13.6-5.5c-2-1.4-7-5.8-9.8-9.7c-2.9-4-7.3-12-7.3-12s2.5,8,4,11.4c0.9,2,3.6,8,7.5,13.2
                    c3.6,4.9,10.7,13.3,21.4,15.1c10.7,1.9,18.1-2.9,19.9-4.1c1.8-1.2,5.7-4.4,8.1-7c2.5-2.7,4.9-6.2,6.3-8.2c1-1.5,2.6-4.6,2.6-4.6
                    L303.4,173.6L303.4,173.6z" />
            </g>
          </svg>
          <br />WebNN Spec
        </a>
      </th>
      <th colspan="4">JavaScript ML Frameworks Integration</th>
    </tr>
    <tr class="title">
      <th colspan="2"><img
          src="https://www.gstatic.com/devrel-devsite/prod/v8ec4d0a037302c47ae529ad4e3f06c9e782b3a31a381294b5a70403547dc6b12/tensorflow/images/lockup.svg">
        Lite for TF.js<br />External Delegate <sup>7</sup></th>
      <th colspan="2"><img src="https://onnxruntime.ai/images/svg/ONNX-Runtime-logo.svg" /><br />Execution Provider
        <sup>8</sup>
      </th>
    </tr>
    <tr class="title">
      <th>Operations
      </th>
      <th>Delegate Version
      </th>
      <th>Operations
      </th>
      <th>EP Version
      </th>
    </tr>
  </thead>
  <tbody id="ops_framework"></tbody>
</table>

<div class="impl_status_framework">
    <div class="title">TensorFlow.js/TFLite<br/>External Delegate</div>
    <div class="title">ONNX Runtime Web<br/>Execution Provider</div>
    <div>
        <div>✅ Supported (<span id="ed_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ed_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="ed_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
    <div>
        <div>✅ Supported (<span id="ep_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ep_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="ep_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
</div> 

<div class="mt-2">
  The total number of WebNN ops is 78. These tables currently lists ops that are implemented or work in progress by multiple backends and JavaScript machine learning frameworks.
</div>

<sup>[1]</sup> XNNPack node definition in [`xnn_define_*`](https://github.com/google/XNNPACK/blob/master/include/xnnpack.h)<br/>
<sup>[2]</sup> [DirectML](https://learn.microsoft.com/en-us/windows/win32/api/_directml/) API<br/>
<sup>[3]</sup> [MLService / TensorFlow Lite Builtin Options](https://source.chromium.org/chromium/chromium/src/+/main:third_party/tflite/src/tensorflow/lite/schema/schema_generated.h;l=1246?q=BuiltinOptions_SoftmaxOptions&ss=chromium%2Fchromium%2Fsrc)<br/>
<sup>[4]</sup> Enabled in [Google Chrome](https://www.google.com/chrome/dev/) and [Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/download/canary) with `#web-machine-learning-neural-network` flag<br/>
<sup>[5]</sup> Enabled in [Google Chrome](https://www.google.com/chrome/canary/) and [Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/download/canary) in command line with flags on Windows 11 21H2 or higher: 
`"%LOCALAPPDATA%\Google\Chrome SxS\Application\chrome.exe" --enable-features=WebMachineLearningNeuralNetwork`<br/>
<sup>[6]</sup> Enabled in [Google Chrome](https://www.google.com/chrome/dev/) with `#web-machine-learning-neural-network` flag<br/>
<sup>[7]</sup> TensorFlow Lite built-in operators [`kTfLiteBuiltin*`](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/delegates/xnnpack/xnnpack_delegate.cc)<br/>
<sup>[8]</sup> ONNX [`Operator Schemas`](https://github.com/onnx/onnx/blob/main/docs/Operators.md) and [`WebNN EP Helper`](https://github.com/microsoft/onnxruntime/blob/main/onnxruntime/core/providers/webnn/builders/helper.h)


<script>
  const qS = (selector) => {
    return document.querySelector(selector);
  }
  
  const qSA = (selector) => {
    return document.querySelectorAll(selector);
  }
  
  const init = () => {
    let ops = document.querySelector('#ops');
    let opsFramework = document.querySelector('#ops_framework');

    let jsonPath = "../assets/json/webnn_status.json";
    if(location.hostname.toLowerCase().indexOf('webmachinelearning.github.io') >-1) 
    {
      jsonPath = "https://webmachinelearning.github.io/assets/json/webnn_status.json";
    }
    fetch(jsonPath)
      .then(response => response.json())
      .then(data => {
        let impl_status = data.impl_status;

        let oplist = '';
        let oplistFramework = '';

        for (let s of impl_status) {

          let spec = `<td class="spec"><a href="https://www.w3.org/TR/webnn/#api-mlgraphbuilder-${s.op_id}">${s.op}</a></td>`

          let wpt = '';
          if (s.wpt_progress === 4) {
            wpt = `<td class="wpt_s">
                      <a href="https://wpt.fyi/results/webnn/${s.wpt}.https.any.html?label=master&amp;label=experimental">📈</a> 
                      <a href="https://github.com/web-platform-tests/wpt/blob/master/webnn/${s.wpt}.https.any.js">🧪</a></td>`
          } 
          if (s.wpt_progress === 3) {
            wpt = `<td class="wpt_wip">🚀🚀</td>`
          }

          let xnnpack = '';
          if (s.xnnpack_op.toString().trim() === "") {
            xnnpack = `<td></td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 4) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `✅ ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '✅ ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_s">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 3) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `🚀 ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '🚀 ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_wip">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 2) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `📅 ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '📅 ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_plan">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else {
            xnnpack = `<td></td><td>${s.xnnpack_chromium_version_added}</td>`;
          }

          let dml = '';
          if (s.dml_op.toString().trim() === "") {
            dml = `<td></td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 4) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `✅ ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '✅ ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_s">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 3) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `🚀 ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '🚀 ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_wip">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 2) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `📅 ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '📅 ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_plan">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else {
            dml = `<td></td><td>${s.dml_chromium_version_added}</td>`;
          }

          let mlservice = '';
          if (s.mlservice_op.toString().trim() === "") {
            mlservice = `<td></td><td>${s.mlservice_chromium_version_added}</td>`;
          } else if (s.mlservice_progress === 4) {
            let mlservice_ops = '';
            if (s.mlservice_op.length > 1) {
              for (let o of s.mlservice_op) {
                mlservice_ops = `✅ ${o} <br/>`;
                mlservice += mlservice_ops;
              }
            } else if (s.mlservice_op.length === 1) {
              mlservice = '✅ ' + s.mlservice_op;
            } else {
              mlservice = ``
            }
            mlservice = `<td class="mlservice_s">${mlservice}</td><td>${s.mlservice_chromium_version_added}</td>`;
          } else if (s.mlservice_progress === 3) {
            let mlservice_ops = '';
            if (s.mlservice_op.length > 1) {
              for (let o of s.mlservice_op) {
                mlservice_ops = `🚀 ${o} <br/>`;
                mlservice += mlservice_ops;
              }
            } else if (s.mlservice_op.length === 1) {
              mlservice = '🚀 ' + s.mlservice_op;
            } else {
              mlservice = ``
            }
            mlservice = `<td class="mlservice_wip">${mlservice}</td><td>${s.mlservice_chromium_version_added}</td>`;
          } else if (s.mlservice_progress === 2) {
            let mlservice_ops = '';
            if (s.mlservice_op.length > 1) {
              for (let o of s.mlservice_op) {
                mlservice_ops = `📅 ${o} <br/>`;
                mlservice += mlservice_ops;
              }
            } else if (s.mlservice_op.length === 1) {
              mlservice = '📅 ' + s.mlservice_op;
            } else {
              mlservice = ``
            }
            mlservice = `<td class="mlservice_plan">${mlservice}</td><td>${s.mlservice_chromium_version_added}</td>`;
          } else {
            mlservice = `<td></td><td>${s.mlservice_chromium_version_added}</td>`;
          }

          let tflite = '';
          if (s.tflite_op.toString().trim() === "") {
            tflite = `<td></td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 4) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `✅ ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '✅ ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_s">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 3) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `🚀 ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '🚀 ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_wip">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 2) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `📅 ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '📅 ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_plan">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else {
            tflite = `<td></td><td>${s.tflite_version_added}</td>`;
          }

          let ort = '';
          if (s.ort_op.toString().trim() === "") {
            ort = `<td></td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 4) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `✅ ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '✅ ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_s">${ort}</td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 3) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `🚀 ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '🚀 ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_wip">${ort}</td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 2) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `📅 ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '📅 ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_plan">${ort}</td><td>${s.ort_version_added}</td>`;
          } else {
            ort = `<td></td><td>${s.ort_version_added}</td>`;
          }

          oplist += `
              <tr>
                ${spec}
                ${wpt}
                ${xnnpack}
                ${dml}
                ${mlservice}
              </tr>
          `;

          oplistFramework += `
              <tr>
                ${spec}
                ${tflite}
                ${ort}
              </tr>
          `;
        }

        oplist = oplist + `
          <tr>
            <th id="spec_total"></th>
            <th id="wpt_total"></th>
            <th id="x_total" colspan="2"></th>
            <th id="dml_total" colspan="2"></th>
            <th id="mlservice_total" colspan="2"></th>
          </tr>
        `;

         oplistFramework = oplistFramework + `
          <tr>
            <th id="spec2_total"></th>
            <th id="ed_total" colspan="2"></th>
            <th id="ep_total" colspan="2"></th>
          </tr>
        `;
        ops.innerHTML = oplist;
        opsFramework.innerHTML = oplistFramework;
        count();
      })
      .catch(console.error);
  }

  const count = () => {
    let spec_defined_total = 78;

    let spec_s = qSA('.spec').length / 2;
    qS('#spec_total').innerHTML = `${spec_s}`;
    qS('#spec2_total').innerHTML = `${spec_s}`;
  
    let wpt_s = qSA('.wpt_s').length;
    let wpt_percentage = (wpt_s / spec_defined_total * 100).toFixed(1) ;
    qS('#wpt_total').innerHTML = `${wpt_s} / ${spec_defined_total}, ${wpt_percentage}%`;

    let x_s = qSA('.x_s').length;
    let x_pi = qSA('.x_pi').length;
    let x_wip = qSA('.x_wip').length;
    let x_percentage = (x_s / spec_defined_total * 100).toFixed(1) ;
    qS('#x_total').innerHTML = `${x_s} / ${spec_defined_total}, ${x_percentage}%`;
    qS('#x_supported').innerHTML = x_s;
    qS('#x_partlyimplemented').innerHTML = x_pi;
    qS('#x_workinprogress').innerHTML = x_wip;
        
    let dml_s = qSA('.dml_s').length;
    let dml_pi = qSA('.dml_pi').length;
    let dml_wip = qSA('.dml_wip').length;
    let dml_percentage = (dml_s / spec_defined_total * 100).toFixed(1) ;
    qS('#dml_total').innerHTML = `${dml_s} / ${spec_defined_total}, ${dml_percentage}%`;
    qS('#dml_supported').innerHTML = dml_s;
    qS('#dml_partlyimplemented').innerHTML = dml_pi;
    qS('#dml_workinprogress').innerHTML = dml_wip;

    let mlservice_s = qSA('.mlservice_s').length;
    let mlservice_pi = qSA('.mlservice_pi').length;
    let mlservice_wip = qSA('.mlservice_wip').length;
    let mlservice_percentage = (mlservice_s / spec_defined_total * 100).toFixed(1) ;
    qS('#mlservice_total').innerHTML = `${mlservice_s} / ${spec_defined_total}, ${mlservice_percentage}%`;
    qS('#mlservice_supported').innerHTML = mlservice_s;
    qS('#mlservice_partlyimplemented').innerHTML = mlservice_pi;
    qS('#mlservice_workinprogress').innerHTML = mlservice_wip;
 
    let ed_s = qSA('.ed_s').length;
    let ed_pi = qSA('.ed_pi').length;
    let ed_wip = qSA('.ed_wip').length;
    let ed_percentage = (ed_s / spec_defined_total * 100).toFixed(1) ;
    qS('#ed_total').innerHTML = `${ed_s} / ${spec_defined_total}, ${ed_percentage}%`;
    qS('#ed_supported').innerHTML = ed_s;
    qS('#ed_partlyimplemented').innerHTML = ed_pi;
    qS('#ed_workinprogress').innerHTML = ed_wip;

    let ep_s = qSA('.ep_s').length;
    let ep_pi = qSA('.ep_pi').length;
    let ep_wip = qSA('.ep_wip').length;
    let ep_percentage = (ep_s / spec_defined_total * 100).toFixed(1) ;
    qS('#ep_total').innerHTML = `${ep_s} / ${spec_defined_total}, ${ep_percentage}%`;
    qS('#ep_supported').innerHTML = ep_s;
    qS('#ep_partlyimplemented').innerHTML = ep_pi;
    qS('#ep_workinprogress').innerHTML = ep_wip;
  }
 document.addEventListener('DOMContentLoaded', init, false);
</script>
