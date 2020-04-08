# mideastancestryscaled
Middle East Ancestry SCALED
<!DOCTYPE html>
<!-- 
https://github.com/vahaduo/
-->
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VahaduoJS 19.11.2</title>
  <style>
    body, html {
      height: 100%;
      margin: 0px;
      background-color: #555;
      font-size: calc(0.5vw + 12px);
      font-family: sans-serif;
      color: #dadada;
    }
    nav {
      width: 100%;
      background-color: #ccc;
      background-image: linear-gradient(#ccc, #ddd);
      padding-top: 0.4em;
      padding-left: 0.4em;
      box-sizing: border-box;
    }
    button {
      outline: none;
      border: none;
      margin: 0px;
      cursor: pointer;
      color: inherit;
    }
    .tablink {
      text-transform: uppercase;
      padding: 0.5em;
      font-size: 1em;
      line-height: 1.4;
      background-color: #555;
    }
    .inactive {
      background: none;
      color: #666;
    }
    .inactive:focus, .inactive:hover {
      background-color: #999;
    }
    .buttons {
      box-sizing: border-box;
      border: none;
      padding: 0.7em;
      margin-bottom: 0.7em;
      font-size: 0.7em;
      color: inherit;
      text-transform: uppercase;
      background-color: #444;
      box-shadow: 2px 2px #333;
    }
    .buttons:focus, .buttons:hover {
      background-image: linear-gradient(#444, #525252);
    }
    .buttons:active {
      color: #555;
      background-color: #999;
      background-image: none;
    }
    #runmulti:disabled, #runalldist:disabled {
      display: none;
    }
    .tabinput {
      box-sizing: border-box;
      border: none;
      margin: 0px;
      outline: 0px;
      padding: 1em;
      height: calc(100% - 4em);
      min-height: 4em;
      width: 100%;
      overflow: auto;
      resize: none;
      color: inherit;
      font-size: 0.7em;
      white-space: pre;
      background: none;
      box-shadow: 0 3px #333;
    }
    #notification {
      font-size: 0.7em;
      box-sizing: border-box;
      margin: 0.7em;
      padding: 0.5em;
      width: calc(100%-1.4em);
      cursor: pointer;
      display: none;
    }
    #notification::before {
      content: "×";
      font-weight: bold;
      margin-right: 1em;
    }
    #multioutput {
      box-sizing: border-box;
      width: 100%;
      padding: 0.7em;
    }    
    .flexcontainer {
      display: flex;
      width: 100%;
    }
    .panel {
      flex-grow: 1;
      box-sizing: border-box;
      padding: 1em;
    }
    .rightpanel {
      max-width: 30em;
    }
    .leftpanel {
      flex-shrink: 0;
      flex-basis: 50%;
    }
    .buttonmulti {
      min-width: 13em;
      margin: 1em 0 0 1em;
    }
    .multiclearok {
      width: 4em;
      margin: 1em 0 0 1em;
    }
    .multiclearcancel {
      width: 8.5em;
      margin: 1em 0 0 0.5em;
    }
    .button100 {
      width: 100%;
    }
    .button80 {
      width: 80%;
    }
    .button20 {
      width: 19%;
      margin-right: 1%;
    }
    .input20 {
      text-align: center;
      width: 20%;
      background-color: #333;
      outline: 0px;
    }
    .input20:focus, .input20:hover {
      background-image: none;
    }
    #distancetargets > button, #singletargets > button {
      text-transform: none;
    }
    table {
      font-size: 0.7em;
      border-spacing: 0em;
    }
    .distances td, .distances th {
      text-align: right;
    }
    .distances td:nth-of-type(2), .distances th:nth-of-type(2) {
      text-align: left;
      padding-left: 0.7em;
    }
    .distances th {
      padding-bottom: 0.7em;
    }
    hr {
      border: 0px;
      border-top: 1px solid #333;
      margin: 0em 0em 1.4em 0em;
    }
    .leftpanel hr:last-of-type, #multioutput hr:last-of-type{
      display: none;
    }
    .barchartmode2 + td {
      padding-left: 0.7em;
    }
    .barchartmode2 {
      min-width: 8em;
    }
    .barchartmode1 {
      width: 100%;
      height: 0.5em;
      box-shadow: inset 1px 1px 0px 0px #444;
    }
    .nonselectable {
      -webkit-touch-callout: none;
      -webkit-user-select: none;
      -khtml-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none;
    }
    .singleinfo {
      font-weight: normal;
    }
    .singleinfo::before {
      content: attr(data-nonselectable);
    }   
    .singleheader {
      text-align: left;
      width: 100%;
      padding-bottom: 0.7em;
    }
    .singleleftcolumn {
      text-align: right;
      padding-right: 0.7em
    }
    .singlerightcolumn {
      text-align: left;
      width: 100%;
    }
    .multitablewrapper {
      overflow-x: auto;
      padding-bottom: 1em;
    }
    .multisources {
      vertical-align: bottom;
      white-space: nowrap;
    }
    .multisources div {
      width: 1em;
      transform: translate(1.5em, -0.5em) rotate(315deg);
    }
    .multisources span, .multiheader span {
      cursor: pointer;
    }
    .multiresult {
      min-width: 2em;
      padding: 0.7em;
      color: white;
      text-align: right;
    }
    .multiheader {
      text-align: center;
      vertical-align: bottom;
      padding-bottom: 0.5em;
    }
    .multitargets {
      padding-right: 1em;
      text-align: right;
      cursor: pointer;
      white-space: nowrap;
    }
    .multidistance {
      padding: 0.7em;
      background-color: #777;
    }
    .multidistchart {
      padding: 0em;
      min-width: 6em;
    }
    @media only screen and (max-width: 639px) {
      .flexcontainer {
        flex-direction: column-reverse;
      }
      .rightpanel {
        max-width: none;
      }
    }
  </style>
  <script>
    let inputHasChanged = false, sourceArray, targetArray, 
      sourceNum, targetNum, dimensions, addGradient = true, 
      printZeroes = false, aggregate = true, addBarChart = 1;
      printZeroesMulti = false, aggregateMulti = true, 
      fastModeMulti = false, cyclesX = 1, cyclesXMulti = 1,
      addDistCol = 1, addDistColMulti = 1;
    
    function showNotification (message, error = 0) {
      const notification = document.getElementById("notification");
      notification.innerHTML = message;
      notification.style.display = "block";
      if (error) {
        notification.style.backgroundColor = "red";
        notification.style.color = "white";
      } else {
        notification.style.backgroundColor = "yellow";
        notification.style.color = "#666";
      }
    }
    
    function clearNotification () {
      const elmnt = document.getElementById("notification");
      elmnt.innerHTML = "";
      elmnt.style.display = "none";
    }
    
    function clearOutput (elmnt, action, display = "block") {
      if (action == "confirm") {
        elmnt.nextElementSibling.style.display = display;
        elmnt.style.display = "none";
      } else if (action == "cancel") {
        elmnt.parentNode.previousElementSibling.style.display = display;
        elmnt.parentNode.style.display = "none";
      } else {
        document.getElementById(action).innerHTML = "";
        elmnt.parentNode.previousElementSibling.style.display = display;
        elmnt.parentNode.style.display = "none";
      }
    }
        
    function toggleOptions (option, elmnt) {
      let msg;
      function toggleOption (currentValue, msg) {
        if (currentValue) {
          elmnt.innerHTML = msg + "no";
        } else {
          elmnt.innerHTML = msg + "yes";
        }
      }
      switch (option) {
        case "printZeroes":
          toggleOption(printZeroes, "print&nbsp;zeroes&nbsp;-&nbsp;");
          printZeroes = !printZeroes;
          break;
        case "aggregate":
          toggleOption(aggregate, "aggregate&nbsp;-&nbsp;");
          aggregate = !aggregate;
          break;
        case "printZeroesMulti":
          toggleOption(printZeroesMulti, "print&nbsp;zeroes&nbsp;-&nbsp;");
          printZeroesMulti = !printZeroesMulti;
          break;
        case "aggregateMulti":
          toggleOption(aggregateMulti, "aggregate&nbsp;-&nbsp;");
          aggregateMulti = !aggregateMulti;
          break;
        case "fastModeMulti":
          toggleOption(fastModeMulti, "fast&nbsp;mode&nbsp;-&nbsp;");
          fastModeMulti = !fastModeMulti;
          break;        
        case "cyclesX":
          cyclesX == 16 ? cyclesX = 1 : cyclesX *= 2;
          elmnt.innerHTML = "cycles&nbsp;-&nbsp;" + cyclesX + "x";
          break;
        case "cyclesXMulti":
          cyclesXMulti == 16 ? cyclesXMulti = 1 : cyclesXMulti *= 2;
          elmnt.innerHTML = "cycles&nbsp;-&nbsp;" + cyclesXMulti + "x";
          break;
        case "addDistCol":
          addDistCol == 16 ? addDistCol = 1 : addDistCol *= 2;
          msg = (addDistCol == 1 ? "no" : addDistCol / 8 + "x");
          elmnt.innerHTML = "add&nbsp;dist&nbsp;col&nbsp;-&nbsp;" + msg;
          break;
        case "addDistColMulti":
          addDistColMulti == 16 ? addDistColMulti = 1 : addDistColMulti *= 2;
          msg = (addDistColMulti == 1 ? "no" : addDistColMulti / 8 + "x");
          elmnt.innerHTML = "add&nbsp;dist&nbsp;col&nbsp;-&nbsp;" + msg;
          break;
        case "addBarChart":
          addBarChart == 2 ? addBarChart = 0 : addBarChart += 1;
          msg = (addBarChart == 0 ? "no" : "mode&nbsp;" + addBarChart);
          elmnt.innerHTML = "add&nbsp;bar&nbsp;chart&nbsp;-&nbsp;" + msg;
          break;
        case "addGradient":
          msg = "add&nbsp;gradient&nbsp;-&nbsp;";
          if (addGradient) {
            elmnt.nextElementSibling.style.display = "none";
            elmnt.innerHTML = msg + "no";
          } else {
            elmnt.nextElementSibling.style.display = "block";
            elmnt.innerHTML = msg + "yes";
          }
          addGradient = !addGradient;
          break;
      }
    }
    
    function validateDistMaxOut (elmnt) {
      const nextValue = Number(elmnt.value.replace(/\,/g,'\.'));
      if (Number.isInteger(nextValue) && nextValue > 0) {
        elmnt.value = nextValue;
      } else {
        elmnt.value = elmnt.defaultValue;
      }
    }
    
    function validateGradFromTo (elmnt) {
      const nextValue = Number(elmnt.value.replace(/\,/g,'\.'));
      if (isNaN(nextValue) || nextValue < 0) {
        elmnt.value = elmnt.defaultValue;
      } else {
        elmnt.value = nextValue;
      }
    }
    
    function dispatcher (elmnt, targetId) {
      if (elmnt.parentNode.id == "distancetargets") {
        distances(targetId);
      } else {
        singleFMC(targetId);
      }
    }
    
    function runAllDist () {
      let i;
      for (i = 0; i < targetNum; i++) {
        distances(i);
      }
    }
    
    function randomFromRange (min, max) {
      return Math.floor(Math.random() * (max - min) ) + min;
    }
    
    function subArray (arr1, arr2) {
      const subtracted = arr1.map(function (elmnt, index) {
        return elmnt - arr2[index];
      });
      return subtracted;
    }
    
    function addArray (arr1, arr2) {
      const added = arr1.map(function (elmnt, index) {
        return elmnt + arr2[index];
      });
      return added;
    }    
    
    function getArraySum (arr) {
      function arrSum (total, num) {
        return total + num;
      }
      return arr.reduce(arrSum);
    }

    function squareArray (arr) {
      const squared = arr.map(function (elmnt) {
        return elmnt * elmnt;
      });
      return squared;
    }
    
    function distances (targetId) {
      let i, n, output = "", resultsNum, getDistance, distanceCurrent, 
        gradStyle1 = "", gradStyle2 = "", gradHSL = "", 
        distMaxOut = document.getElementById("distmaxout").value;
      const target = targetArray[targetId].slice(), 
        distances = Array(sourceNum).fill([]), 
        gradFrom = document.getElementById("gradfrom").value, 
        gradTo = document.getElementById("gradto").value; 
      for (i = 0; i < sourceNum; i++) {
        getDistance = subArray(target, sourceArray[i]);
        getDistance.shift();
        getDistance = squareArray(getDistance);
        getDistance = getArraySum(getDistance);
        getDistance = Math.sqrt(getDistance);
        distances[i] = distances[i].concat(sourceArray[i][0]);
        distances[i].push(getDistance);
      }
      distances.sort(function(a, b) {
        return a[1] - b[1];
      });
      resultsNum = sourceNum;
      if (target[0] === distances[0][0]) {
        distances.shift();
        resultsNum--;
      }
      if (resultsNum < distMaxOut) {
       distMaxOut = resultsNum;
      }
      if (addGradient) {
        gradStyle1 = ' style="color:black;background-color:hsl(';
        gradStyle2 = ', 100%, 50%)"';
      }
      output += '<table class="distances"><tr><th>Distance&nbsp;to:</th><th>' + target[0] + "</th>";
      for (i = 0; i < distMaxOut; i++) {
        distanceCurrent = distances[i][1];
        if (addGradient) {
          if (distanceCurrent < gradFrom) {
            gradHSL = 120;
          } else if (distanceCurrent > gradTo) {
            gradHSL = 240;
          } else {
            gradHSL = 120 -(((distanceCurrent - gradFrom) / (gradTo - gradFrom)) * 240);
          }
        }
        output += "<tr><td" + gradStyle1 + gradHSL + gradStyle2 + ">" + distanceCurrent.toFixed(8) + "</td><td>" + distances[i][0] + "</td></tr>";
      }
      output += "</table>";
      printOutput(output, "distanceoutput");
    }
    
    function prepareTarget (targetId, slots) {
      let i;
      const target = targetArray[targetId].slice();
      target.shift();
      for (i = 0; i < dimensions; i++) {
        target[i] = target[i] / slots;
      }
      return target;
    }
    
    function prepareSource (slots) {
      let i, j, tempLine;
      const source = Array(sourceNum);
      for (i = 0; i < sourceNum; i++) {
        tempLine = sourceArray[i].slice();
        tempLine.shift();
        source[i] = tempLine.slice();
        for (j = 0; j < dimensions; j++) {
          source[i][j] = source[i][j] / slots;
        }
      }
      return source;
    }
    
    function fastMonteCarlo (target, source, targetId, slots, cyclesMultiplier, distColMultiplier) {
      let i, j, tempLine, currentSlots, currentPoint, currentDistance, nextSlots, 
        nextPoint, nextDistance, previousDistance, rankingNum, dimNum = dimensions; 
      const cycles = sourceNum * cyclesMultiplier, scores = Array(sourceNum).fill(0),
        result = {target: targetId, distance, scores}, ranking = Array(),
        bigNumber = 100000000000000000;
      if (distColMultiplier) {
        distColMultiplier /= 8;
        dimNum++;
        for (i = 0; i < sourceNum; i++) {
          source[i] = subArray(source[i], target);
          source[i].push(distColMultiplier * Math.sqrt(distance(source[i])));
        }
      }
      else {
        for (i = 0; i < sourceNum; i++) {
          source[i] = subArray(source[i], target);
        }
      }

      function randomizedSlots (oldSlots) {
        let i, newSlots = Array(slots);
        for (i = 0; i < slots; i++) {
          newSlots[i] = randomFromRange(0, sourceNum);
          while (newSlots[i] == oldSlots[i]){
            newSlots[i] = randomFromRange(0, sourceNum);
          }
        }
        return newSlots;
      }
      
      function buildPoint (fromSlots) {
        let i, tempLine, newPoint = Array(dimNum).fill(0);
        for (i = 0; i < slots; i++) {
          tempLine = source[fromSlots[i]].slice();
          newPoint = addArray(newPoint, tempLine);
        }
        return newPoint;
      }
      
      function distance (fromPoint) {
        let dist = squareArray(fromPoint);
        dist = getArraySum(dist);
        return dist;
      }
      
      if (sourceNum == 1) {
        currentSlots = Array(slots).fill(0);
        currentPoint = buildPoint(currentSlots);
        currentDistance = distance(currentPoint);
        scores[0] = 1;
        result.distance = Number(Math.sqrt(currentDistance).toFixed(8));
        result.scores = scores;
        return result;
      }
      currentSlots = Array(slots).fill(-1);
      currentSlots = randomizedSlots(currentSlots);
      currentPoint = buildPoint(currentSlots);
      currentDistance = distance(currentPoint);
      for (i = 0; i < cycles; i++) {
        nextSlots = randomizedSlots(currentSlots);
        for (j = 0; j < slots; j++) {
          nextPoint = subArray(currentPoint, source[currentSlots[j]]);
          nextPoint = addArray(nextPoint, source[nextSlots[j]]);
          nextDistance = distance(nextPoint);
          if (nextDistance < currentDistance) {
            currentSlots[j] = nextSlots[j];
            currentPoint = nextPoint;
            currentDistance = nextDistance;
          }
        }
      }
      for (i = 0; i < slots; i++) {
        scores[currentSlots[i]] += 1;
      }
      for (i = 0; i < sourceNum; i++) {
        if (scores[i] > 0) {
          ranking.push([i, scores[i]]);
        }
      }
      ranking.sort(function(a, b) {
        return b[1] - a[1];
      });
      rankingNum = ranking.length;
      currentDistance = Math.round(bigNumber * currentDistance);
      do {
        previousDistance = currentDistance;
        for (i = rankingNum -1; i > -1; i--) {
          if (ranking[i][1] > 0) {
            for (j = 0; j < rankingNum; j++) {
              if (i == j) {continue;}
              nextPoint = subArray(currentPoint, source[ranking[i][0]]);
              nextPoint = addArray(nextPoint, source[ranking[j][0]]);
              nextDistance = Math.round(bigNumber * distance(nextPoint));
              if (nextDistance < currentDistance) {
                ranking[i][1]--;
                ranking[j][1]++;
                currentPoint = nextPoint;
                currentDistance = nextDistance;
                break;
              }
            }
          }
        }
      }
      while (currentDistance < previousDistance);
      for (i = 0; i < rankingNum; i++) {
        scores[ranking[i][0]] = ranking[i][1];
      }
      for (i = 0; i < sourceNum; i++) {
        scores[i] =  scores[i] / slots;
      }
      if (distColMultiplier) {currentPoint.pop();}
      currentDistance = distance(currentPoint);
      result.distance = Number(Math.sqrt(currentDistance).toFixed(8));
      result.scores = scores;
      return result;
    }
    
    function multiFMC () {
      let i, j, source, target, slots, resultsTable = Array(sourceNum), 
        sourceNumLocal = sourceNum, outputMsg, tempLine, accumulatedResult, 
        currentResult, longestSourceName = 0, averageDistance = 0, 
        minDistance, maxDistance, currentDistance, names = "", 
        namesDiv, namesCompStyle, namesOffset;
      const results = Array(targetNum), 
        addDC = (addDistColMulti == 1 ? false : addDistColMulti);
      slots = (fastModeMulti ? 125 : 500);
      for (i = 0; i < targetNum; i++) {
        source = prepareSource(slots);
        target = prepareTarget(i, slots);
        results[i] = fastMonteCarlo(target, source, i, slots, cyclesXMulti, addDC);
      }
      for (i = 0; i < sourceNum; i++) {
        resultsTable[i] = Array(targetNum + 1);
        resultsTable[i][0] = sourceArray[i][0];
        for (j = 0; j < targetNum; j++) {
          resultsTable[i][j + 1] = results[j].scores[i];
        }
      }
      if (aggregateMulti) {
        resultsTable = aggregateResults(resultsTable, sourceNumLocal);
        sourceNumLocal = resultsTable.length;
      }
      
      function returnHSL (currentResult) {
        if (currentResult == 0) {
          return '#444455';
        } else {
          return 'hsl(' + (225 - 35 * currentResult) + ', ' + (25 + 70 * currentResult) + '%, ' + (45 * currentResult + 35) + '%)';
        }
      }
      
      function returnDistChart (currentDistance, maxDistance, minDistance, averageDistance) {
        let averageDistancePct, currentDistancePct;
        if (maxDistance == minDistance) {
          maxDistance = 1;
          minDistance = 0;
          averageDistance = 0.5;
          currentDistance = 0.5;
        }
        function getDistancePct (distance) {
          return ((distance - minDistance) / (maxDistance - minDistance)) * 80;
        }
        averageDistancePct = getDistancePct(averageDistance);
        currentDistancePct = getDistancePct(currentDistance);
        return '<td class="nonselectable multidistchart" style="background-image: linear-gradient(90deg, #777 ' + (averageDistancePct + 3) + '%, #999 '+ (averageDistancePct + 3) +'%, #999 '+ (averageDistancePct + 7) + '%, #777 ' + (averageDistancePct + 7) + '%);"><div style="padding-left: ' + (((currentDistancePct + 5) * 6 / 100) - 0.3) + 'em">&#8226;</div></td>';
      }
      
      accumulatedResult = Array(sourceNumLocal).fill(0);
      minDistance = results[0].distance;
      maxDistance = results[0].distance;
      for (i = 0; i < targetNum; i++) {
        currentDistance = results[i].distance;
        averageDistance += currentDistance;
        if (currentDistance > maxDistance) {
          maxDistance = currentDistance;
        }
        if (currentDistance < minDistance) {
          minDistance = currentDistance;
        }
        for (j = 0; j < sourceNumLocal; j++) {
          accumulatedResult[j] += resultsTable[j][i + 1];
        }
      }
      averageDistance = (averageDistance / targetNum).toFixed(8);
      if (!printZeroesMulti) {
        for (i = sourceNumLocal - 1; i > -1; i--) {
          if (accumulatedResult[i] == 0) {
            resultsTable.splice(i, 1);
            accumulatedResult.splice(i, 1);
          }
        }
        sourceNumLocal = resultsTable.length;
      }
      for (i = 0; i < sourceNumLocal; i++) {
        names += resultsTable[i][0] + "<br>";
      }
      namesDiv = document.createElement("div");
      namesDiv.innerHTML = names;
      namesDiv.style.cssText = "font-size: 0.7em; width: auto; overflow: hidden; max-height: 1em; min-height: 1em; position: absolute; left: -999em; top: -999em; display: table-cell";
      document.body.appendChild(namesDiv);
      namesCompStyle = window.getComputedStyle(namesDiv);
      namesOffset = Number((namesCompStyle.getPropertyValue("width")).replace(/px/, "")) / Number((namesCompStyle.getPropertyValue("height")).replace(/px/, "")) / 1.4142 + 2;
      document.body.removeChild(namesDiv);
      outputMsg = '<div class="multitablewrapper"><table><tr style="height:' + namesOffset + 'em"><td data-columnid="0" class="multiheader"><div><span onclick="sortByColumn(this, false)">Target</span></div></td><td data-columnid="1" class="multiheader" colspan="2"><div><span onclick="sortByColumn(this)">Distance' + (addDistColMulti == 1 ? "" : " | ADC: " + addDistColMulti / 8 + "x") + '</span></div></td>';
      for (i = 0; i < sourceNumLocal; i++) {
          outputMsg += '<td data-columnid="' + (i + 2) + '" class="multisources"><div><span onclick="sortByColumn(this)">' + resultsTable[i][0] + '</span></div></td>';
      }
      outputMsg += '</tr>';
      for (i = 0; i < targetNum; i++) {
        currentDistance = results[i].distance;
        outputMsg += '<tr data-rowid="' + i + '"><td onclick="sortByRow(this)" data-columnid="0" class="multitargets">' + targetArray[i][0] + '</td><td data-columnid="1" class="multidistance">' + currentDistance.toFixed(8) + '</td>' + returnDistChart(currentDistance, maxDistance, minDistance, averageDistance);
        for (j = 0; j < sourceNumLocal; j++) {
            currentResult = resultsTable[j][i + 1];
            outputMsg += '<td data-columnid="' + (j + 2) + '" class="multiresult" style="background-color:' + returnHSL(currentResult) + '">' + (100 * currentResult).toFixed(1) + '</td>';
        }
        outputMsg += '</tr>';
      }
      outputMsg += '<tr><td onclick="sortByRow(this, true)" data-columnid="0" class="multitargets">Average</td><td data-columnid="1" class="multidistance">' + averageDistance + '</td>' + returnDistChart(averageDistance, maxDistance, minDistance, averageDistance);
      for (i = 0; i < sourceNumLocal; i++) {
          currentResult = accumulatedResult[i] / targetNum;
          outputMsg += '<td data-columnid="' + (i + 2) + '" data-average="' + currentResult + '" class="multiresult" style="background-color:' + returnHSL(currentResult) + '">' + (100 * currentResult).toFixed(1) + '</td>';
      }
      outputMsg += '</tr>';
      outputMsg += '</table><button onclick="resetSorting(this)" class="buttons buttonmulti">reset&nbsp;sorting</button><button onclick= "copyTable(this)" class="buttons buttonmulti">copy&nbsp;table&nbsp;as&nbsp;CSV</button><button onclick= "copyTable(this, true)" class="buttons buttonmulti">copy&nbsp;table&nbsp;as&nbsp;TSV</button></div>';
      printOutput(outputMsg, "multioutput");
    }
    
    function aggregateResults (resultsTable, sourceNumLocal) {
      let popName, storedName;
      for (i = 0; i < sourceNumLocal; i++) {
        popName = resultsTable[i][0].split(":");
        resultsTable[i][0] = popName[0];
      }
      resultsTable.sort( function(a, b) {
        return a[0].localeCompare(b[0]);
      });
      for (i = sourceNumLocal - 2; i > -1; i--) {
        if (resultsTable[i][0] == resultsTable[i + 1][0]) {
          storedName = resultsTable[i][0];
          resultsTable[i] = addArray(resultsTable[i],resultsTable[i + 1]);
          resultsTable[i][0] = storedName;
          resultsTable.splice(i + 1, 1);
        }
      }
      return resultsTable;
    }
    
    function sortByRow (elmnt, average = false) {
      let i, j, rowLen, rowNum, ranking, cell;
      const table = elmnt.parentNode.parentNode, 
        row = elmnt.parentNode.cells;
      rowLen = row.length;
      ranking = Array(rowLen).fill([]);
      if (average) {
        for (i = 0; i < rowLen; i++) {
          ranking[i] = ranking[i].concat([row[i].dataset.columnid]);
          ranking[i].push(Number(row[i].dataset.average));
        }
      } else {
        for (i = 0; i < rowLen; i++) {
          ranking[i] = ranking[i].concat([row[i].dataset.columnid]);
          ranking[i].push(Number(row[i].innerHTML));
        }
      }
      ranking.splice(0, 3);
      ranking = sortByNum(ranking);
      rowNum = table.rows.length;
      rowLen = ranking.length;
      for (i = 0; i < rowNum; i++) {
        for (j = 0; j < rowLen; j++) {
          cell = table.rows[i].querySelector('[data-columnid="' + ranking[j][0] + '"]');
          cell.parentNode.appendChild(cell);
        }
      }      
    }
    
    function sortByColumn (elmnt, byNumber = true) {
      let i, column, columnLen, ranking, row;
      elmnt = elmnt.parentNode.parentNode;
      const table = elmnt.parentNode.parentNode,
        columnid = elmnt.dataset.columnid;
      column = table.querySelectorAll('[data-columnid="' + columnid + '"]');
      columnLen = column.length;
      ranking = Array(columnLen).fill([]);
      for (i = 1; i < columnLen; i++) {
        ranking[i] = ranking[i].concat([column[i].parentNode.dataset.rowid]);
        ranking[i].push((byNumber ? Number(column[i].innerHTML) : column[i].innerHTML));
      }
      ranking.shift();
      ranking.pop();
      columnLen -= 2;

      function sortByText(arr) {
        const storeArr = arr.toString();
        arr.sort( function(a, b) {
          return a[1].localeCompare(b[1]);
        });
        if (storeArr == arr.toString()) {
          arr.sort( function(a, b) {
            return b[1].localeCompare(a[1]);
          });
        }
        return arr;
      }
      
      ranking = (byNumber ? sortByNum(ranking, (columnid == 1 ? false : true)) : sortByText(ranking));
      for (i = 0; i < columnLen; i++) {
        row = table.querySelector('[data-rowid="' + ranking[i][0] + '"]');
        table.appendChild(row);
      }
      row = table.rows[1];
      table.appendChild(row);
    }
    
    function sortByNum(arr, desc = true) {
      const storeArr = arr.toString();
      function sortDesc (arr) {
        arr.sort( function(a, b) {
          return b[1] - a[1];
        });
        return arr;
      }
      function sortAsc (arr) {
        arr.sort( function(a, b) {
          return a[1] - b[1];
        });
        return arr;
      }
      arr = (desc ? sortDesc(arr) : sortAsc(arr));
      if (storeArr == arr.toString()) {
        arr = (desc ? sortAsc(arr) : sortDesc(arr));
      }
      return arr;
    }
    
    function resetSorting (elmnt) {
      let i, j, n, table, rowLen, row, columnLen, cell;
      table = elmnt.parentNode.querySelector("tr").parentNode;
      rowLen = table.rows.length;
      for (i = 0, n = rowLen - 2; i < n; i++) {
        row = table.querySelector('[data-rowid="' + i + '"]');
        table.appendChild(row);
      }
      row = table.rows[1];
      table.appendChild(row);
      columnLen = table.rows[0].cells.length;
      for (i = 0; i < rowLen; i++) {
        for (j = 2; j < columnLen; j++) {
          cell = table.rows[i].querySelector('[data-columnid="' + j + '"]');
          cell.parentNode.appendChild(cell);
        }
      }
    }
    
    function copyTable (elmnt, TSV = false) {
      let tableText;
      const textarea = document.createElement("textarea");
      tableText = elmnt.parentNode.querySelector("tr").parentNode.innerHTML;
      tableText = tableText.replace(/<\/td>/g,",").replace(/<\/tr>/g,"\n")
        .replace(/<([^>]+)>/g,"").replace(/&#8226;,/g,"").replace(/•,/g,"")
        .replace(/,\n/g,"\n");
      if (TSV) {
        tableText = tableText.replace(/,/g,"\t");
      }
      textarea.value = tableText;
      textarea.setAttribute("readonly", "");
      textarea.style.cssText = "position: absolute; top: -999em; left: -999em";
      document.body.appendChild(textarea);
      textarea.select();
      document.execCommand("copy");
      document.body.removeChild(textarea);
    }
    
    function singleFMC (targetId) {
      let i, outputMsg, currentResult, sourceNumLocal = sourceNum, 
        resultsTable = Array(sourceNumLocal);
      const  slots = 500,
        target = prepareTarget(targetId, slots),
        source = prepareSource(slots),
        addDC = (addDistCol == 1 ? false : addDistCol),
        result = fastMonteCarlo(target, source, targetId, slots, cyclesX, addDC);
      for (i = 0; i < sourceNumLocal; i++) {
        resultsTable[i] = Array(2);
        resultsTable[i][0] = sourceArray[i][0];
        resultsTable[i][1] = result.scores[i];
      }
      if (aggregate) {
        resultsTable = aggregateResults(resultsTable, sourceNumLocal);
        sourceNumLocal = resultsTable.length;
      }
      resultsTable.sort( function(a, b) {
        return b[1] - a[1];
      });
      outputMsg = "<table><tr><th colspan='" + (addBarChart == 2 ? 3 : 2) + "' class='singleheader'>Target: " + targetArray[targetId][0] + "<br/>";
      outputMsg += "Distance: " + (100 * result.distance).toFixed(4) + "% / " + result.distance.toFixed(8) + (addDistCol == 1 ? "" : " | ADC: " + addDistCol / 8 + "x") + "<br/>";
      outputMsg += '<div class="singleinfo nonselectable" data-nonselectable="' + 'Sources: ' + sourceNum + ' Cycles: ' + sourceNum * cyclesX + '"></div>';
      outputMsg += "</th></tr>";
      for (i = 0; i < sourceNumLocal; i++) {
        if (printZeroes || resultsTable[i][1] != 0) {
          currentResult = resultsTable[i][1] * 100;
          outputMsg += "<tr>"
          outputMsg += (addBarChart == 2 ? '<td class="barchartmode2 nonselectable" style="background-image: linear-gradient(90deg, #aaa ' + currentResult + '%, #444 '+ currentResult +'%);"></td>' : '');
          outputMsg += '<td class="singleleftcolumn">' + currentResult.toFixed(1) + '</td><td class="singlerightcolumn">' + resultsTable[i][0] + '</td>';
          outputMsg += (addBarChart == 1 ? '<tr><td colspan= "2" class="barchartmode1 nonselectable" style="background-image: linear-gradient(90deg, #ff7f00 '+ currentResult +'%, #666 '+ currentResult +'%);"></td></tr>' : '');
        }
      }
      outputMsg += "</table>"
      printOutput(outputMsg, "singleoutput");
    }
    
    function printOutput (what, where) {
      const output = document.getElementById(where);
      output.innerHTML = what + "<br><hr>" + output.innerHTML;
    }
    
    function processInput () {
      if (!inputHasChanged) {
        return;
      }
      let errors = 0, message = "";
      
      function clearTargetButtons () {
        document.getElementById("distancetargets").innerHTML = "";
        document.getElementById("singletargets").innerHTML = "";
        document.getElementById("runmulti").disabled = true;
        document.getElementById("runalldist").disabled = true;
      }
      
      function textareaToArray (textareaId) {
        let i, j, m, n, text1, text2, diff12, 
          text3, diff23, text4, diff34, lines, columnNum;
        const textarea = document.getElementById(textareaId);
        textareaId = textareaId.toUpperCase();
        text1 = textarea.value.trim().replace(/\r\n/g,"\n").replace(/\"/g,"").replace(/\</g, "&lt;").replace(/\>/g, "&gt;");
        text2 = text1.replace(/[^\S\n]/g, "");
        diff12 = text1.length - text2.length;
        if (diff12 > 0) {
          message += "WARNING! Number of white-space characters removed in " + textareaId + " data: "+diff12+". ";
        }
        text3 = text2.replace(/\n+/g, "\n");
        diff23 = text2.length - text3.length;
        if (diff23 > 0) {
          message += "WARNING! Number of empty lines removed in " + textareaId + " data: " + diff23 + ". ";
        }
        text4 = text3.replace(/\,+/g, "\,");
        diff34 = text3.length - text4.length;
        if (diff34 > 0) {
          message += "ERROR! Number of missing values in " + textareaId + " data: " + diff34 + ". ";
          errors = 1;
          return;
        }
        lines = text4.split("\n");
        columnNum = lines[0].split(",").length;
        if (columnNum === 1) {
          message += "ERROR! Data load error in " + textareaId + ". ";
          errors = 1;
          return;
        }
        for (i = 0, n = lines.length; i < n; i++) {
          lines[i] = lines[i].split(",");
          if (lines[i].length !== columnNum) {
            message += "ERROR! Variable column number in " + textareaId + " data. ";
            errors = 1;
            return;
          }
          for (j = 1, m = lines[i].length; j < m; j++) {
            if (isNaN(lines[i][j])) {
              message += "ERROR! Non-numerical value detected in " + textareaId + " data. ";
              errors = 1;
              return;
            }
          }
        }
        for (i = 0, n = lines.length; i < n; i++) {
          for (j = 1; j < columnNum; j++) {
            lines[i][j] = Number(lines[i][j]);
          }
        }
        return lines;
      }
      
      sourceArray = textareaToArray("source");
      targetArray = textareaToArray("target");
      if (errors) {
        clearTargetButtons();
        showNotification(message, 1);
        return;
      } else if (sourceArray[0].length !== targetArray[0].length) {
        clearTargetButtons();
        message += "ERROR! Column number mismatch.";
        showNotification(message, 1);
        return;
      } else {
        let targets = "", i;
        clearNotification();
        if (message.length > 0) {
          showNotification(message);
        }
        sourceNum = sourceArray.length;
        targetNum = targetArray.length;
        dimensions = sourceArray[0].length - 1;
        for (i = 0; i < targetNum; i++) {
          targets = targets + '<button class="buttons button100" onclick="dispatcher(this,' + i + ')">' + targetArray[i][0] + '</button>';
        }
        document.getElementById("distancetargets").innerHTML = targets;
        document.getElementById("singletargets").innerHTML = targets;
        document.getElementById("runmulti").disabled = false;
        document.getElementById("runalldist").disabled = false;
        inputHasChanged = false;
      }
    }
    
    function openTab (tabid, button) {
      let i, n;
      const tabs = document.getElementsByClassName("tab"), 
        tablinks = document.getElementsByClassName("tablink");
      for (i = 0, n = tabs.length; i < n; i++) {
        tabs[i].style.display = "none";
      }
      for (i = 0, n = tablinks.length; i < n; i++) {
        tablinks[i].classList.add("inactive");
      }
      document.getElementById(tabid).style.display = "block";
      document.getElementById(tabid).focus();
      button.classList.remove("inactive");
    }
    
    function initialize () {
      document.getElementById("defaulttab").click();
      if (document.getElementById("source").value.length > 0 || document.getElementById("target").value.length > 0 ) {
        inputHasChanged = true;
      } 
    }
  </script>
</head>
<body>
  <nav>
    <button class="tablink" onclick="openTab('source', this)" id="defaulttab">source</button><!--
    --><button class="tablink" onclick="openTab('target', this)">target</button><!--
    --><button class="tablink" onclick="openTab('distance', this);processInput()">distance</button><!--
    --><button class="tablink" onclick="openTab('single', this);processInput()">single</button><!--
    --><button class="tablink" onclick="openTab('multi', this);processInput()">multi</button>  
  </nav>
  <div id="notification" onclick="clearNotification()"></div>
  <textarea onchange="inputHasChanged = true" class="tab tabinput" id="source" spellcheck="false" placeholder=" Paste data here. Comma-separated values, no header."></textarea>
  Amerindian,0.052359,-0.328016,0.109742,0.073644,-0.104635,-0.016733,-0.202344,-0.242528,-0.002659,-0.015672,0.00682,-0.004946,0.005649,0.000413,-0.014658,-0.002652,-0.000261,0.005828,0.01257,0.006378,0.002371,-0.009892,-0.00419,0.005784,0.007305
Amerindian,0.056912,-0.312783,0.11917,0.093024,-0.114791,-0.014502,-0.301519,-0.359293,-0.009613,-0.016401,-0.000325,0.000899,-0.004608,0.023121,-0.013572,0.003447,0.00691,0.000253,-0.00176,0.002501,-0.001497,0.004081,0.003697,0.000361,-0.007544
Assyrian,0.093335,0.137096,-0.059208,-0.065892,-0.036007,-0.011992,0.0047,-0.007384,-0.02168,-0.003645,0.004709,-0.003447,-0.003419,0.005092,0.005157,0.002121,-0.011735,0.004561,0.007919,-0.015382,0.000125,0.005564,0.001849,-0.006989,-0.000359
Azeri,0.094473,0.092413,-0.051666,-0.031654,-0.041238,-0.003068,0.00423,-0.009692,-0.02802,-0.010387,-0.002598,-0.002698,-0.00223,-0.000138,0.002036,-0.001458,-0.014733,0.004181,0.009553,-0.009129,0.001497,-0.002473,-0.002588,-0.006386,0.003233
Balochi,0.085367,0.063978,-0.093903,0.028424,-0.071398,0.029562,0.00893,0.006,-0.025156,-0.016037,-0.00065,-0.003447,0.006838,-0.007707,0.019137,0.027976,-0.012126,0.002534,0.008673,-0.025262,-0.000998,-0.017188,0.001725,-0.014098,0.016765
Bedouin,0.0387,0.127957,-0.04714,-0.080104,-0.018465,-0.029284,-0.011751,-0.00923,0.026384,0,0.012179,-0.006594,0.018137,0.009221,0.00285,-0.001326,-0.003651,0,0.003771,0.003502,-0.001622,-0.000495,-0.001109,-0.003133,0.001796
Brahui,0.064879,0.04773,-0.103708,0.032946,-0.075091,0.027052,0.00329,-0.001846,-0.01943,-0.019317,-0.007145,-0.007793,0.0055,-0.006468,0.021037,0.028374,-0.013169,0.002787,0.002388,-0.025137,0.003619,-0.01051,-0.003697,-0.016026,0.008861
EastEuro,0.130897,0.128972,0.084098,0.054264,0.045855,0.03765,0.011281,0.011076,-0.000818,-0.018406,-0.013153,-0.013188,0.000595,0.011423,-0.009908,0.007027,0.025686,-0.003547,0.002388,0.002501,-0.003494,-0.003957,0.003328,-0.005061,-0.013771
EastEuro,0.130897,0.137096,0.071653,0.05168,0.03139,0.014223,0.00893,0.006,0.00225,-0.012028,-0.007145,-0.010491,0.015312,0.00578,-0.004479,0.005304,0.01708,0.000253,0.002137,0.009379,-0.004492,-0.00272,0.006409,0.001566,-0.006826
Egyptian,0.004553,0.142174,-0.050534,-0.09044,-0.005847,-0.033467,-0.00423,0.000231,0.02986,-0.000364,0.01088,-0.017534,0.02438,0.000413,0.010993,0.003845,-0.009388,-0.007601,-0.010433,-0.000875,-0.000749,-0.006306,0.008258,0.003856,-0.003832
Egyptian_Karaite,0.083091,0.141159,-0.042615,-0.072675,-0.005232,-0.023427,0.00141,-0.002308,0.000205,0.011845,0.008444,-0.007343,0.009366,0.005643,-0.008686,-0.001193,-0.006519,-0.006334,0.004777,-0.003502,-0.00861,0.002226,-0.005053,0.003856,-0.005149
GeorgianJew,0.100164,0.136081,-0.056568,-0.062662,-0.028005,-0.013945,0.004465,-0.011538,-0.023316,-0.012392,0.002923,0.00045,0.002527,0.001101,0.005293,0.011668,0.005346,0.00038,0.000503,0.006753,0.008111,0.007296,0.000123,-0.004217,-0.001557
Iranian_Bandari,0.05805,0.091398,-0.079195,-0.009367,-0.058472,0.005857,0.004935,-0.003923,-0.037223,-0.018224,-0.000812,0.002248,0.000297,0.000275,0.010315,0.022938,-0.005737,0.003547,0.002765,-0.008504,0.007986,-0.001978,0.008011,-0.00723,0.002395
IranianJew,0.088782,0.136081,-0.065242,-0.069122,-0.029236,-0.016455,0.001645,-0.002308,-0.01084,0.002734,0.011205,-0.001049,0.007284,-0.001101,-0.016015,0.001458,-0.007693,0.002914,0.001383,-0.005378,-0.000125,0.004699,-0.006902,-0.006145,-0.003233
Kurdish,0.095611,0.116786,-0.069767,-0.040375,-0.046162,-0.00502,0.010105,-0.010846,-0.027611,-0.007289,-0.001624,0.001499,-0.006838,-0.007844,0.0038,0.012861,0.005607,0.001774,0.001885,-0.008879,0.002121,-0.003586,0.006162,0.001205,0.006706
Lebanese,0.091058,0.144205,-0.054305,-0.076874,-0.013233,-0.034861,0,-0.013153,0.00225,0.01385,0.004709,-0.007194,0.000446,-0.000413,-0.014929,0.012331,-0.000391,0.002027,0.001257,-0.004127,0.000749,0.006059,0,0,0.002515
Lebanese,0.083091,0.14319,-0.046386,-0.062985,-0.018465,-0.022869,-0.005405,-0.006461,-0.001636,0.005832,0.003248,-0.007194,0.009812,0.002202,-0.002986,0.004641,-0.001956,0,0.002765,0.003126,-0.000624,0.001113,-0.006162,0.006748,-0.005029
Makrani,0.062603,0.058901,-0.103708,0.023902,-0.067089,0.018965,0.005405,-0.001154,-0.026384,-0.01385,0.000325,-0.007044,0.010109,-0.010046,0.020358,0.042163,0.001956,0.003421,0.004148,-0.03139,0.001248,-0.018053,-0.000246,-0.023979,0.015807
Northafrican,-0.034147,0.140143,-0.009051,-0.081073,0.02462,-0.035698,-0.030786,0.009461,0.07097,0.036083,0.00406,-0.006894,0.027056,-0.01101,0.013029,-0.009281,0.003129,-0.028885,-0.048771,0.013006,-0.024706,-0.037219,0.018734,-0.00494,0.016885
Northafrican,-0.126344,0.127957,0.006411,-0.052326,0.020619,-0.018128,-0.037132,0.025384,0.05604,0.027335,0.006171,0.002098,0.018731,-0.01156,0.017644,-0.01843,-0.00339,-0.027998,-0.033813,0.007379,0.000873,-0.024607,0.020952,0.005302,-0.00012
Northafrican,-0.33464,0.096475,0.000754,-0.040698,0.030775,-0.008088,-0.036897,0.032076,0.014112,0.017495,0.003085,-0.004046,0.0333,-0.011147,0.016965,-0.021877,-0.001173,-0.012035,-0.023757,-0.00075,-0.010981,-0.026585,0.016269,-0.002651,0.001197
NorthwestEuro,0.141141,0.138112,0.064111,0.050065,0.031083,0.014502,0.006815,0.004154,0,0.005832,0.002111,0.010641,-0.017096,-0.017753,0.013572,0.006232,0.004303,0.008488,-0.006411,0.003001,0.009982,0.004575,0.002465,0.007471,0.005868
NorthwestEuro,0.129758,0.12491,0.064488,0.05168,0.040315,0.021475,-0.001175,0.006461,0.006136,-0.003098,-0.003897,0,-0.010555,-0.004542,0.020629,-0.001061,-0.021774,0.004307,-0.000126,-0.004252,0.000873,0.004328,-0.001479,0.016147,0.003592
Palestinian,0.050082,0.13405,-0.044877,-0.075905,-0.014156,-0.028726,-0.006345,-0.006692,0.012271,-0.004738,0.007145,-0.001798,0.019475,0.004954,-0.013708,-0.001591,-0.012647,0.003674,-0.004022,0.004252,0.004866,0.007172,-0.011832,0.000361,0.005508
Parsi_India,0.078538,0.061947,-0.091263,0.006783,-0.052317,0.016176,0.004465,0.001385,-0.00634,-0.006378,-0.006008,-0.000599,0.011001,-0.002752,0.00095,0.020021,0.000391,0.001774,0.004022,-0.004377,0.000125,-0.000124,0.003204,0.001566,0.002515
Parsi_Pakistan,0.068294,0.053823,-0.097297,0.008721,-0.048932,0.008088,0.001175,0.000923,-0.009408,-0.010205,-0.001949,-0.005995,0.008028,-0.001789,0.005972,0.007425,-0.010822,0.005068,0.006159,-0.009755,-0.000749,-0.002597,-0.002711,-0.010845,0.002994
Pashtun,0.076261,0.014217,-0.105217,0.07106,-0.067705,0.04267,0.000235,0.000231,-0.014521,-0.007836,-0.000812,0.004946,-0.001784,-0.00055,0.008143,0.010342,-0.000391,0.00038,0.003394,-0.016508,-0.006364,-0.006677,0.002835,0.001928,-0.002634
Persian,0.078538,0.083273,-0.059962,-0.015827,-0.039392,0.00502,0.00752,-0.001615,-0.025361,-0.020593,-0.001949,-0.002698,0.009663,-0.004404,0.003257,0.014452,-0.006519,0.00114,-0.002137,0.004252,0.000749,-0.001113,0.006655,-0.001205,-0.000479
Saudi,0.047806,0.144205,-0.058077,-0.113051,-0.013541,-0.052153,-0.010575,-0.003692,0.057267,-0.008201,0.017376,-0.029374,0.066303,0.006744,0.008686,0.018828,-0.032726,0.003547,-0.004148,0.029764,0.01984,0.019413,-0.004437,0.008073,-0.013532
Syrian,0.081953,0.126941,-0.052043,-0.056525,-0.023081,-0.012829,-0.00329,-0.001615,-0.001432,-0.005649,0.001786,-0.002997,0.003271,-0.003441,-0.0019,0.022142,0.008214,0.012289,0.005908,0.001501,-0.00861,0.002597,-0.001109,0.005904,-0.001676
SyrianJew,0.08992,0.142174,-0.026776,-0.062339,-0.001846,-0.020638,-0.005405,-0.003692,0.002659,0.012028,0.005684,0.001349,0.005054,0.00289,0.001493,-0.006762,-0.007432,-0.001267,-0.003142,-0.004252,-0.002121,-0.001484,0.006532,-0.003012,0.001197
SoutheastEuro,0.105855,0.146236,-0.003017,-0.046189,0.018465,-0.013945,0.00188,-0.004615,0.007772,0.021868,0.005359,0.006594,-0.015312,0.000963,-0.007329,-0.006497,0.000522,-0.004054,0.005405,-0.005503,0.00025,0.001484,-0.002588,0.005422,-0.000599
SoutheastEuro,0.117238,0.146236,0.012068,-0.019703,0.016003,-0.005578,-0.00094,-0.003231,-0.000409,0.019681,-0.001786,0.005545,-0.006987,0.005643,-0.011808,0.001061,0.008736,-0.001014,0.005531,-0.003377,-0.007112,-0.004575,0.000493,0.001325,-0.003832
SouthwestEuro,0.105855,0.144205,0.039221,-0.007106,0.041546,-0.001673,-0.00094,0.009461,0.032315,0.034443,0.002273,0.006744,-0.007879,-0.007707,0.009229,-0.006629,-0.014473,-0.00266,-0.007919,5e-04,-0.000125,0.001237,0.003328,-0.001205,0.002874
SouthwestEuro,0.119514,0.146236,0.040729,0.00323,0.043085,0.000558,0.00141,0.003461,0.020248,0.034443,0.002273,0.008093,-0.014123,-0.020919,0.009772,-0.001724,0.001043,-0.001394,-0.006285,0.00025,0.003369,0.000742,-0.002465,-0.002771,-0.005149
Subsaharian,-0.628304,0.061947,0.021496,0.01615,-0.001539,0.003347,-0.042067,0.049152,-0.050108,0.030616,-0.000974,0.003897,0.023191,-0.006468,0.00475,-0.004773,0.005737,-0.007601,0.00729,-0.002876,0.004991,0.000495,-0.006409,0.002771,-0.005029
Subsaharian,-0.577083,0.051792,-0.001886,-0.006137,-0.005539,-0.003626,-0.015041,0.018922,0.077719,-0.096767,-0.025008,0.019183,-0.040882,-0.001789,0.008822,-0.015911,0.021644,-0.009755,0.022877,-0.025262,0.001622,0.002844,-0.001109,0.003856,0.006466
Turkish,0.087644,0.059916,-0.032809,-0.040052,-0.031083,-0.017012,0.00846,-0.002538,-0.016975,0.006925,-0.003248,0.01169,-0.005649,0.000688,0.002714,0.000398,0.00678,-0.005194,-0.001383,-0.002001,-0.000499,-0.004081,-0.008504,0.006025,-0.000359
Turkish,0.104717,0.12491,0.006411,-0.00969,0.008001,-0.01004,0.00423,-0.003461,-0.002045,0.00492,0.009094,0.003447,-0.001041,0.005505,-0.007057,-0.000398,0.002217,0.008488,0.008296,-0.001751,-0.006613,0.002968,-0.001602,-0.004217,0.003233
WestEuro,0.133173,0.133034,0.048649,0.012597,0.042777,0.010598,0.00282,0.005538,0.014317,0.006196,0,0.004796,-0.018583,-0.003028,0.013572,-0.00358,-0.019427,-0.005574,-0.01257,-0.011005,-0.000624,0.000989,-0.00419,0.018557,-0.008263
Yemenite,0.060326,0.139128,-0.071653,-0.112082,-0.005539,-0.061077,-0.004465,-0.005769,0.058289,-0.009841,0.017051,-0.040014,0.066749,0.008808,0.019272,0.023601,-0.029858,0.00152,-0.002891,0.014507,0.015722,0.018424,-0.016392,0.003976,-0.006107
Yemenite,0.045529,0.146236,-0.056945,-0.12048,-0.006463,-0.047969,-0.006815,-0.002769,0.048063,-0.007472,0.012991,-0.032071,0.05441,0.011698,0.00665,0.024396,-0.02386,0.001774,0.001006,0.021635,0.008485,0.016446,-0.008258,0.00482,-0.005987
YemeniteJew,0.040976,0.142174,-0.058077,-0.119511,-0.011079,-0.056615,-0.008695,-0.005307,0.060335,-0.009476,0.014615,-0.025627,0.057383,0.005367,0.000407,0.019225,-0.037551,0.005448,0.012067,0.019759,0.02558,0.02337,-0.013434,-0.002771,-0.007305
 <textarea onchange="inputHasChanged = true" class="tab tabinput" id="target" spellcheck="false" placeholder=" Paste data here. Comma-separated values, no header."></textarea>
  <div class="tab" id="distance">
    <div class="flexcontainer">
      <div class="panel leftpanel" id="distanceoutput"></div>
      <div class="panel rightpanel">
        <button class="buttons button100" onclick="clearOutput(this, 'confirm')">clear&nbsp;output</button>
        <div style="display: none">
          <button class="buttons button20" onclick="clearOutput(this, 'distanceoutput')">ok</button><!--
          --><button class="buttons button80" onclick="clearOutput(this, 'cancel')">cancel</button>
        </div>
        <button class="buttons button80" onclick="this.nextElementSibling.focus()">max output number:</button><!--
        --><input spellcheck="false" class="buttons input20" id="distmaxout" value="25" onblur="validateDistMaxOut(this)">
        <button class="buttons button100" onclick="toggleOptions('addGradient', this)">add gradient - yes</button>
        <div>
          <button class="buttons button80" onclick="this.nextElementSibling.focus()">gradient from:</button><!--
          --><input spellcheck="false" class="buttons input20" id="gradfrom" value="0" onblur="validateGradFromTo(this)">
          <button class="buttons button80" onclick="this.nextElementSibling.focus()">gradient to:</button><!--
          --><input spellcheck="false" class="buttons input20" id="gradto" value="0.2" onblur="validateGradFromTo(this)">
        </div>
        <button id="runalldist" disabled="true" class="buttons button100" onclick="runAllDist()">run&nbsp;all</button>
        <div id="distancetargets"></div>
      </div>
    </div>
  </div>
  <div class="tab" id="single">
    <div class="flexcontainer">
      <div class="panel leftpanel" id="singleoutput"></div>
      <div class="panel rightpanel">
        <button class="buttons button100" onclick="clearOutput(this, 'confirm')">clear&nbsp;output</button>
        <div style="display: none"><!--
          --><button class="buttons button20" onclick="clearOutput(this, 'singleoutput')">ok</button><!--
          --><button class="buttons button80" onclick="clearOutput(this, 'cancel')">cancel</button><!--
        --></div><!--
        --><button class="buttons button100" onclick="toggleOptions('cyclesX', this)">cycles&nbsp;-&nbsp;1x</button><!--
        --><button class="buttons button100" onclick="toggleOptions('addDistCol', this)">add&nbsp;dist&nbsp;col&nbsp;-&nbsp;no</button><!--
        --><button class="buttons button100" onclick="toggleOptions('printZeroes', this)">print zeroes&nbsp;-&nbsp;no</button><!--
        --><button class="buttons button100" onclick="toggleOptions('aggregate', this)">aggregate&nbsp;-&nbsp;yes</button><!--
        --><button class="buttons button100" onclick="toggleOptions('addBarChart', this)">add&nbsp;bar&nbsp;chart&nbsp;-&nbsp;mode&nbsp;1</button>
        <div id="singletargets"></div>
      </div>
    </div>
  </div>
  <div class="tab" id="multi">
    <button class="buttons buttonmulti" onclick="clearOutput(this, 'confirm', 'inline-block')">clear output</button><!--
        --><div style="display: none;"><!--
          --><button class="buttons multiclearok" onclick="clearOutput(this, 'multioutput', 'inline-block')">ok</button><!--
          --><button class="buttons multiclearcancel" onclick="clearOutput(this, 'cancel', 'inline-block')">cancel</button><!--
        --></div><!--
    --><button class="buttons buttonmulti" onclick="toggleOptions('cyclesXMulti', this)">cycles&nbsp;-&nbsp;1x</button><!--
    --><button class="buttons buttonmulti" onclick="toggleOptions('addDistColMulti', this)">add&nbsp;dist&nbsp;col&nbsp;-&nbsp;no</button><!--
    --><button class="buttons buttonmulti" onclick="toggleOptions('fastModeMulti', this)">fast&nbsp;mode&nbsp;-&nbsp;no</button><!--
    --><button class="buttons buttonmulti" onclick="toggleOptions('printZeroesMulti', this)">print&nbsp;zeroes&nbsp;-&nbsp;no</button><!--
    --><button class="buttons buttonmulti" onclick="toggleOptions('aggregateMulti', this)">aggregate&nbsp;-&nbsp;yes</button><!--
    --><button id="runmulti" disabled="true" class="buttons buttonmulti" onclick="multiFMC()">run</button>
    <div id="multioutput"></div>
  </div>
  <script>
    initialize();
  </script>
</body>
</html>
