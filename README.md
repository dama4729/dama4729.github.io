<!DOCTYPE html>

<html>
<head>
    <title>Schmidt arrangements</title>

    <script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://github.com/devongovett/pdfkit/releases/download/v0.6.2/pdfkit.js"></script>
    <script src="https://github.com/devongovett/blob-stream/releases/download/v0.1.2/blob-stream-v0.1.2.js"></script>
    <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <style type="text/css">


        body {
            margin: 0;
            font-family: "Times New Roman", Times, serif;
            background-color: #FFFFFF;
            font-size: 90%;
        }

        * {
            box-sizing: border-box;
            padding: 0;
        }


        .inline {
            float: left;
        }

        .after-inline {
            clear: left;
        }

        ul, li {
            margin: 0;
            padding: 0;
        }

        ul {
            display: table;
        }

        li {
            list-style-position: inside;
            display: table-row;
        }

            li::before {
                content: "\2022";
                display: table-cell;
                text-align: right;
                padding-right: .3em;
            }

        .column {
            padding: 1%;
        }

        .left {
            float: left;
            width: 19em;
        }

        .right {
            float: right;
            width: 27em;
        }

        .middle {
            margin-left: 19em;
            margin-right: 27em;
        }

        .row:after {
            content: "";
            display: table;
            clear: both;
        }

        table {
            border-collapse: collapse;
            font-size: 1em;
        }

            table:hover {
                cursor: default;
            }

            table.table1, table.table1 td, table.table1 tr {
                text-align: center;
                border: 1px solid black;
            }

                table.table1 td {
                    width: 1.5em;
                    height: 1.5em;
                }

            table.table3 {
                position: absolute;
                left: 0.2em;
                top: 50%;
                transform: translateY(-50%);
                width: 100%;
            }

                table.table3, table.table3 td, table.table3 tr {
                    height: 1.6em;
                    border-style: none;
                    padding-right: 0.5em;
                    vertical-align: middle;
                    text-align: left;
                }

        .toggle0, .toggle1 {
            border: 1px solid black;
            background-color: white;
            padding: 0.3em;
        }

        .toggle0 {
            border-bottom: none;
        }

        .toggle1 {
            border-top: none;
        }


        .h1, .h2 {
            text-align: left;
            background-color: #c3cbd8;
            position: relative;
            padding: 0.2em;
            border: 1px solid black;
        }

        .h1 {
            border-bottom-style: none;
        }

        .button {
            position: relative;
            font-family: "Times New Roman", Times, serif;
            text-align: center;
            width: 1.3em;
            height: 1.3em;
            float: right;
        }

        .button, .checkBox {
            border: 1px solid #b3b3b3;
            -webkit-border-radius: 2px;
            -moz-border-radius: 2px;
            border-radius: 2px;
            padding-top: 0.05em;
            text-decoration: none;
            background-color: #f7f7f7;
            background-image: -webkit-gradient(linear, left top, left bottom, from(#f7f7f7), to(#e0e0e0));
            background-image: -webkit-linear-gradient(top, #f7f7f7, #e0e0e0);
            background-image: -moz-linear-gradient(top, #f7f7f7, #e0e0e0);
            background-image: -ms-linear-gradient(top, #f7f7f7, #e0e0e0);
            background-image: -o-linear-gradient(top, #f7f7f7, #e0e0e0);
            background-image: linear-gradient(to bottom, #f7f7f7, #e0e0e0);
            filter: progid:DXImageTransform.Microsoft.gradient(GradientType=0,startColorstr=#f7f7f7, endColorstr=#e0e0e0);
        }

            .button:hover, .checkBox:hover {
                border: 1px solid #6b6b6b;
            }

            .button:active, .checkBox:active {
                border: 1px solid #6b6b6b;
                background-color: #E6E6E6;
                background-image: -webkit-gradient(linear, left top, left bottom, from(#E6E6E6), to(#CCCCCC));
                background-image: -webkit-linear-gradient(top, #E6E6E6, #CCCCCC);
                background-image: -moz-linear-gradient(top, #E6E6E6, #CCCCCC);
                background-image: -ms-linear-gradient(top, #E6E6E6, #CCCCCC);
                background-image: -o-linear-gradient(top, #E6E6E6, #CCCCCC);
                background-image: linear-gradient(to bottom, #E6E6E6, #CCCCCC);
                filter: progid:DXImageTransform.Microsoft.gradient(GradientType=0,startColorstr=#E6E6E6, endColorstr=#CCCCCC);
            }

        .stayActive {
            border: 1px solid #6b6b6b;
            background-color: #E6E6E6;
            background-image: -webkit-gradient(linear, left top, left bottom, from(#E6E6E6), to(#CCCCCC));
            background-image: -webkit-linear-gradient(top, #E6E6E6, #CCCCCC);
            background-image: -moz-linear-gradient(top, #E6E6E6, #CCCCCC);
            background-image: -ms-linear-gradient(top, #E6E6E6, #CCCCCC);
            background-image: -o-linear-gradient(top, #E6E6E6, #CCCCCC);
            background-image: linear-gradient(to bottom, #E6E6E6, #CCCCCC);
            filter: progid:DXImageTransform.Microsoft.gradient(GradientType=0,startColorstr=#E6E6E6, endColorstr=#CCCCCC);
        }

        .checkBox {
            width: 0.75em;
            height: 0.75em;
            position: relative;
        }

        .arrow {
            position: absolute;
            right: 0.2em;
            top: 50%;
            transform: translateY(-50%);
            -moz-transform: translateY(-50%);
            pointer-events: none;
            width: 0.5em;
            height: 0.5em;
        }

        .checkmark {
            position: absolute;
            width: 0.54em;
            height: 0.78em;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            pointer-events: none;
        }

        .icon {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            -moz-transform: translate(-50%,-50%);
            pointer-events: none;
        }

        .textBox {
            font-size: 1em;
            height: 1.3em;
            padding-left: 0.2em;
            font-family: "Times New Roman", Times, serif;
            border-style: none;
        }

        .rgbText {
            text-align: center;
            height: 1.1em;
            font-family: "Times New Roman", Times, serif;
            font-size: 1em;
            border: 1px solid black;
        }

        .discText {
            border-style: none;
            text-align: center;
            font-size: 1em;
            position: absolute;
            width: 1.65em;
            overflow: hidden;
            left: 8.35em;
            top: 0.37em;
            height: 1.1em;
            font-family: "Times New Roman", Times, serif;
        }

        input:focus {
            outline: none;
        }

        table.table2 tr {
            vertical-align: middle;
        }

        table.table2 td {
            position: relative;
            height: 1.3em;
        }

        table.table4 {
            border: 1px solid black;
            font-size: 1em;
            background-color: #FFF;
        }

            table.table4 th {
                border: 1px solid black;
                font-weight: normal;
                position: relative;
            }

            table.table4 th, table.table4 td {
                text-align: left;
                padding-left: 0.1em;
                vertical-align: middle;
            }

        table.matrix {
            border-left: 1px solid black;
            border-right: 1px solid black;
        }

            table.matrix td {
                text-align: center;
                vertical-align: middle;
            }

        .swatch {
            width: 0.7em;
            height: 0.7em;
            margin: 0;
            padding: 0;
            outline-width: 0.06em;
            outline-color: black;
        }

        .colorBar {
            margin-top: 0.4em;
            width: 15.8em;
            height: 0.5em;
            position: relative;
        }

        .superScript {
            position: relative;
            left: -0.5em;
            font-size: 0.6em;
            pointer-events: none;
        }

        .subScript {
            font-size: 0.6em;
            pointer-events: none;
        }

        .overline {
            text-decoration: overline;
            pointer-events: none;
        }

        .noscroll {
            position: fixed;
            overflow-y: scroll;
            width: 100%;
        }

        .canvasContain, .colorContain, .alphaContain {
            position: relative;
            width: 100%;
            overflow: hidden;
        }

            .canvasContain:after, .colorContain:after, .alphaContain:after {
                content: "";
                display: block;
            }

            .canvasContain:after {
                padding-bottom: 100%;
            }

            .colorContain:after {
                padding-bottom: 83.54%;
            }

            .alphaContain:after {
                padding-bottom: 12.96%;
            }

        .canvas {
            position: absolute;
            top: 0;
            left: 0;
            overflow: hidden;
        }

        .cayleyEntry {
            width: 1.5em;
            height: 1.5em;
            pointer-events: none;
        }

        .wait * {
            cursor: wait;
        }

        .disable * {
            pointer-events: none;
        }

        .infoNumber {
            position: absolute;
            left: 0;
            top: 0;
            display: block;
            visibility: hidden;
            width: 1.5em;
            height: 1.5em;
            padding: 0.1em;
            font-size: 0.6em;
            border: 1px solid black;
            text-align: center;
            background-color: white;
            font-weight: bold;
            pointer-events: none;
        }

            .infoNumber:hover {
                cursor: default;
            }

        .infoDisplay {
            visibility: hidden;
            padding-left: 2px;
            padding-right: 2px;
            border: 1px solid black;
            font-size: 0.7em;
            position: absolute;
            background-color: white;
            pointer-events: none;
            white-space: nowrap;
            z-index: 1000;
        }

        .infoCell {
            text-align: left;
            padding-top: 0.2em;
            padding-bottom: 0.2em;
        }

        .infoRow > td {
            padding-bottom: 0.3em;
            padding-top: 0.3em;
        }

        .describe {
            position: absolute;
            display: none;
            left: 50%;
            transform: translateX(-50%);
            top: -1.5em;
            font-size: 0.6em;
            background-color: white;
            overflow: hidden;
            white-space: nowrap;
            padding: 0.1em;
        }

        .modes{
            width:100%;
        }

        .mode td {
            vertical-align: middle;
            text-align: center;
            width: 33.333%;
        }
    </style>
</head>

<body>

    <div id="waitWrap" style="visibility:hidden;min-width:72.5em;">
        <div style="width:100%;text-align:center;font-size:1.5em;padding-top:10px;">Extended Schmidt Arrangements</div>
        <div class="row">
            <div class="column left">
                <div class="h1" style="padding-top:0.1em;">
                    <span style="pointer-events:none;">
                        Field:<math><mspace width="0.3em"><mi>&#x1d43e;</mi><mo>=</mo><mi>&#8474; (</mi><msqrt><mo mathsize="0.8em">-</mo><mspace width="1.8em" height="0.9em" /></msqrt><mspace width="0.2em" /><mi mathvariant="normal">)</mi></math>
                    </span>
                    <div class="button" id="draw" style="margin-top:0.1em">
                        <object class="icon" type="image/svg+xml" data="draw.svg" style="width:1em;height:1.2em"></object>
                    </div>
                    <input type="text" class="discText" id="disc" />
                </div>

                <div class="h1">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Arrangements</span></div>
                    <div class="button" onclick="tog(0,1)">
                        <img src="downarrow.jpg" id="arrow0,1" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle0" id="toggle0,1" style="display:none;">
                    <div id="menus"></div>
                </div>

                <div class="h1">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Window</span></div>
                    <div class="button" onclick="tog(0,2)">
                        <img src="downarrow.jpg" id="arrow0,2" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle0" id="toggle0,2" style="display: none">
                    <table class="table2">
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox2,0" onclick="check(2,0)"></div></td>
                            <td>Full Canvas</td>
                        </tr>
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox2,1" onclick="check(2,1)"></div></td>
                            <td>Strip</td>
                        </tr>
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox2,2" onclick="check(2,2)"></div></td>
                            <td>Parallelogram</td>
                        </tr>
                    </table>
                </div>

                <div class="h2">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Color</span></div>
                    <div class="button" onclick="tog(0,3)">
                        <img src="downarrow.jpg" id="arrow0,3" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle1" id="toggle0,3" style="display:none;padding-bottom:0;">
                    <table class="table2" style="margin-top:0.4em;margin-bottom:0.4em;width:100%;">
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox3,0" onclick="check(3,0)"></div></td>
                            <td style="width:4.5em;">Border</td>
                            <td onmousedown="toggleColors(0,0)"><div id="swatch0" class="swatch" style="background-color:black;" onmouseover="highlight(2,0,0)" onmouseout="highlight(2,0,1)"></div></td>
                            <td style="text-align:right;">
                                rgb(&nbsp;<input type="text" class="rgbText" id="rgb0" onmousedown="toggleColors(1,0)" style="width:5.4em;" />&nbsp;)
                            </td>
                        </tr>
                        <tr style="font-size:20%"><td></td><td></td><td></td><td></td></tr>
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox3,1" onclick="check(3,1)"></div></td>
                            <td style="width:4.5em;">Canvas</td>
                            <td onmousedown="toggleColors(0,1)"><div id="swatch1" class="swatch" style="background-color:black;" onmouseover="highlight(2,1,0)" onmouseout="highlight(2,1,1)"></div></td>
                            <td style="text-align:right;">
                                rgb(&nbsp;<input type="text" class="rgbText" id="rgb1" onmousedown="toggleColors(1,1)" style="width:5.4em;" />&nbsp;)
                            </td>
                        </tr>
                        <tr style="font-size:20%"><td></td><td></td><td></td><td></td></tr>
                    </table>
                    <div id="elementList" style="height:1.6em;width:2.4em;margin:0 auto;position:relative;"></div>
                    <table class="table2" style="margin-top:0.4em;width:100%;">
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox3,2" onclick="check(3,2)"></div></td>
                            <td style="width:4.5em;">Stroke</td>
                            <td onmousedown="toggleColors(0,2)"><div id="swatch2" class="swatch" onmouseover="highlight(2,2,0)" onmouseout="highlight(2,2,1)"></div></td>
                            <td style="text-align:right;">
                                rgb(&nbsp;<input type="text" class="rgbText" id="rgb2" onmousedown="toggleColors(1, 2)" style="width:5.4em;" />&nbsp;)
                            </td>
                        </tr>
                        <tr style="font-size:20%"><td></td><td></td><td></td><td></td></tr>
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox3,3" onclick="check(3,3)"></div></td>
                            <td style="width:4.5em;">Fill</td>
                            <td onmousedown="toggleColors(0,3)"><div id="swatch3" class="swatch" onmouseover="highlight(2,3,0)" onmouseout="highlight(2,3,1)"></div></td>
                            <td style="text-align:right;">
                                rgb(&nbsp;<input type="text" class="rgbText" id="rgb3" onmousedown="toggleColors(1, 3)" style="width:5.4em;" />&nbsp;)
                            </td>
                        </tr>
                        <tr style="font-size:20%"><td></td><td></td><td></td><td></td></tr>
                        <tr>
                            <td style="width:1.4em;"><div class="checkBox" id="checkBox3,4" onclick="check(3,4)"></div></td>
                            <td style="width:4.5em;">Glow*</td>
                            <td onmousedown="toggleColors(0,4)"><div id="swatch4" class="swatch" onmouseover="highlight(2,4,0)" onmouseout="highlight(2,4,1)"></div></td>
                            <td style="text-align:right;">
                                rgb(&nbsp;<input type="text" class="rgbText" id="rgb4" onmousedown="toggleColors(1,4)" style="width:5.4em;" />&nbsp;)
                            </td>
                        </tr>
                        <tr style="font-size:20%"><td></td><td></td><td></td><td></td></tr>
                    </table>
                    <div id="colorPick">
                        <div id="toggleColors" class="colorContain" style="display:none;">
                            <svg xmlns="http://www.w3.org/2000/svg" class="canvas" viewBox="0 0 158 132" preserveAspectRatio="none" width="100%" height="100%">
                                <defs>
                                    <pattern id="img" patternUnits="userSpaceOnUse" width="133" height="131">
                                        <image xlink:href="colorWheel.png" x="2" y="0" width="131" height="131" />
                                    </pattern>
                                    <linearGradient id="gradient" x1="0%" y1="0%" x2="0%" y2="100%" spreadMethod="pad">
                                        <stop id="stopBlack" offset="0%" style="stop-color:rgb(0,255,0);stop-opacity:1" />
                                        <stop offset="100%" style="stop-color:rgb(0,0,0);stop-opacity:1" />
                                    </linearGradient>
                                </defs>
                                <circle id="colorWheel" cx="68" cy="66" r="65" fill="url(#img)" stroke="none" />
                                <circle cx="68" cy="66" r="65.7" fill="none" stroke="white" stroke-width="2" />
                                <rect id="colorBar" x="143" y="1.5" width="12" height="129" fill="url(#gradient)" stroke="none" />
                                <circle id="wheelPick" cx="55" cy="66" r="1.6" fill="none" stroke="black" stroke-width="1" style="pointer-events:none" />
                                <rect id="barPick" x="142.5" y="4" width="13" height="2" fill="none" stroke="black" stroke-width="1" style="pointer-events:none" />
                            </svg>
                        </div>
                        <div id="toggleAlpha" class="alphaContain" style="display:none;">
                            <svg xmlns="http://www.w3.org/2000/svg" class="canvas" id="alphaBar" viewBox="0 0 162 21" preserveAspectRatio="none" width="100%" height="100%">
                                <filter id="blurFilter" x="-100%" y="-100%" width="300%" height="300%">
                                    <feGaussianBlur id="stdDevPick" in="SourceGraphic" stdDeviation="1" />
                                </filter>
                                <rect x="4" y="9" width="151" height="3" rx="1.5" ry="1.5" fill="gray" stroke="none" style="pointer-events:none" />
                                <circle id="blurPick" cx="6" cy="10.5" r="3" fill="none" stroke="black" stroke-width="2" filter="url(#blurFilter)" style="pointer-events:none;" />
                                <circle id="alphaPick" cx="6" cy="10.5" r="3" fill="rgba(0,0,0,0)" stroke="black" stroke-width="0.5" style="pointer-events:none" />
                            </svg>
                        </div>
                    </div>
                    <div style="font-size:0.8em;">*Expect significant performance loss.</div>
                </div>
            </div>

            <div class="column right">

                <div class="h1">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Group Structure</span></div>
                    <div class="button" onclick="tog(0,6)">
                        <img src="downarrow.jpg" id="arrow0,6" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle0" id="toggle0,6" style="display: none">
                    <div id="structure" style="pointer-events:none;"></div>
                </div>

                <div class="h1">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Cayley Table</span></div>
                    <div class="button" onclick="tog(0,7)">
                        <img src="downarrow.jpg" id="arrow0,7" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle0" id="toggle0,7" style="display: none">
                    <div id="cayley"></div>
                </div>

                <div class="h2">
                    <div style="height:1.3em;display:inline-block;padding-top:0.1em;"><span style="pointer-events:none;">Notes</span></div>
                    <div class="button" onclick="tog(0,8)">
                        <img src="downarrow.jpg" id="arrow0,8" style="width:0.5em;height:0.5em">
                    </div>
                </div>
                <div class="toggle1" id="toggle0,8" style="display:block;font-size:0.8em;padding-left:0;padding-right:0;">
                    <div id="notes" style="padding-left:0.3em;padding-right:0.3em;overflow:auto;">
                        <ul>
                            <li>Type a positive integer from 1 to 100 in the "Field" box and click the "Draw" icon.</li>

                            <li>Adjust the type and number of arrangements in the "Arrangements" box.</li>
                            <li>Download options are below the canvas. For high resolution images, download as a PDF and convert externally.</li>
                            <li>This is a work in progress. If a feature that intersets you is not functioning, email daniel.e.martin at colorado dot edu.</li>
                        </ul>
                    </div>
                    <div id="transition" style="margin-top:0.5em;display:none;width:100%;background-color:white;padding:0.3em;border-top:1px solid black;">
                        <div>Transition matrix:</div>
                        <div style="width:100%;">
                            <table style="margin:0 auto;">
                                <tr style="vertical-align:middle;">
                                    <td style="position:relative;width:3.1em;">
                                        <table class="table4" style="position:absolute;left:0;top:0.4em;">
                                            <tr>
                                                <th onclick="tog(7,7)">
                                                    <div id="header7" data-value="0" style="padding-left:0.2em;height:1.3em;width:2.5em;">&#x1d440;<sub class='subScript'>1</sub></div>
                                                    <img src="downarrow.jpg" class="arrow" id="arrow7,7">
                                                </th>
                                            </tr>
                                            <tbody id="toggle7,7" style="display:none"></tbody>
                                        </table>
                                    </td>
                                    <td>
                                        <table class="matrix">
                                            <tr style="padding-bottom:0.2em;">
                                                <td style="width:0.3em;border-top:1px solid black;"></td>
                                                <td id="entry0" style="padding-right:0.3em;"></td>
                                                <td id="entry1"></td>
                                                <td style="width:0.3em;border-top:1px solid black;"></td>
                                            </tr>
                                            <tr>
                                                <td style="width:0.3em;border-bottom:1px solid black;"></td>
                                                <td id="entry2" style="padding-right:0.3em;"></td>
                                                <td id="entry3"></td>
                                                <td style="width:0.3em;border-bottom:1px solid black;"></td>
                                            </tr>
                                        </table>
                                    </td>
                                    <td style="width:1.2em;text-align:center;">=</td>
                                    <td id="detNorm" style="padding-right:0.1em;"></td>
                                    <td style="position:relative;width:2.5em;">
                                        <table class="table4" style="position:absolute;left:0;top:0.4em;">
                                            <tr>
                                                <th onclick="tog(8,8)">
                                                    <div id="header8" data-value="1" style="padding-left:0.2em;height:1.3em;width:2.5em;">&#x1d440;<sub class='subScript'>2</sub></div>
                                                    <img src="downarrow.jpg" class="arrow" id="arrow8,8">
                                                </th>
                                            </tr>
                                            <tbody id="toggle8,8" style="display:none"></tbody>
                                        </table>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>


                <p id="demo"></p>
            </div>

            <div class="column middle" id="middle">
                <div class="h2" style="height:1.8em;">
                    <table class="modes">
                        <tr>
                            <td>
                                <div id="artsy" class="button" style="float:none;margin: 0 auto;" onclick="artsy()" onmouseover="describe(3)" onmouseout="describe(3)">
                                    <div id="describe3" class="describe">Canvas</div>
                                    <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" style="pointer-events:none;" viewBox="0 0 1 1">
                                        <circle stroke="rgb(4,38,230)" stroke-width="0.04" fill="none" cx="0.7" cy="0.2253" r="0.18"></circle>
                                        <circle stroke="rgb(4,38,230)" stroke-width="0.04" fill="none" cx="0.4" cy="0.6" r="0.3"></circle>
                                        <circle stroke="rgb(4,38,230)" stroke-width="0.04" fill="none" cx="0.536364" cy="0.42968" r="0.081818"></circle>
                                        <circle stroke="rgb(4,38,230)" stroke-width="0.04" fill="none" cx="0.8123" cy="0.68" r="0.12"></circle>
                                        <circle stroke="rgb(4,38,230)" stroke-width="0.04" fill="none" cx="0.2" cy="0.23068" r="0.12"></circle>
                                    </svg>
                                </div>
                            </td>
                            <td>
                                <div id="cFrac" class="button" style="float:none;margin: 0 auto;" onclick="cFrac()" onmouseover="describe(2)" onmouseout="describe(2)">
                                    <div id="describe2" class="describe">Ideal covers</div>
                                    <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" style="pointer-events:none;" viewBox="0 0 1 1">
                                        <circle stroke="none" fill="rgba(13,220,60,0.7)" cx="0.5" cy="0.3" r="0.25"></circle>
                                        <circle stroke="none" fill="rgba(0,0,255,0.5)" cx="0.6" cy="0.6" r="0.35"></circle>
                                        <circle stroke="none" fill="rgba(255,0,100,0.5)" cx="0.3" cy="0.5" r="0.25"></circle>
                                    </svg>
                                </div>
                            </td>
                            <td>
                                <div class="button" id="info" style="float:none;margin: 0 auto;" onclick="info()" onmouseover="describe(1)" onmouseout="describe(1)">
                                    <div id="describe1" class="describe">Information</div>
                                    <img src="info.png" style="width:1em;height:0.8em">
                                </div>
                            </td>
                        </tr>
                    </table>
                </div>
                <br />
                <div id="canvasContain" class="canvasContain">
                    <svg id="canvas" class="canvas" width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" style="z-index:0">
                        <filter id="blurHL" x="-200%" y="-200%" width="500%" height="500%">
                            <feGaussianBlur id="stdDevHL" in="SourceGraphic" stdDeviation="0.005" />
                        </filter>
                        <rect id="background" x="0" y="0" fill="none" stroke="none" />
                        <g id="arrangement"></g>
                        <g id="infoCircles"></g>
                        <g id="selectCircles"></g>
                        <g id="points"></g>
                        <g id="blur" filter="url(#blurHL)" style="visiblity:hidden;pointer-events:none;"><circle stroke="none" fill="none"></circle></g>
                        <g id="stroke" style="visiblity:hidden;pointer-events:none;"> <circle stroke="none" fill="none"></circle></g>
                        <g id="infoLabels"></g>
                        <g id="selectLabels"></g>
                        <svg id="viewer" xmlns="http://www.w3.org/2000/svg"></svg>
                    </svg>
                    <div id="curvContain" style="width:10em;position:absolute;bottom:2em;left:50%;transform:translateX(-50%);display:none;pointer-events:none;">
                        <table style="float:left;border: 1px solid black;background-color:#FFF;text-align:center;pointer-events:auto">
                            <tr id="addWheel" style="vertical-align:middle;">
                                <td id="curvWheel" style="height:1.4em;width:3.5em;position:relative;">
                                    <input type="text" class="textBox" id="curv" value="20" style="float:left;width:2.7em;height:100%;" />
                                    <img src="uparrow.jpg" id="curvUp" style="position:absolute;top:0.1em;right:0.15em;width:0.5em;height:0.5em">
                                    <img src="downarrow.jpg" id="curvDown" style="position:absolute;bottom:0.1em;right:0.15em;width:0.5em;height:0.5em">
                                </td>
                            </tr>
                        </table>
                        <table style="float:right;border: 1px solid black;background-color:#FFF;text-align:center;pointer-events:auto">
                            <tr style="vertical-align:middle"><td onclick="reset()" style="height:1.4em;width:3em;">Reset</td></tr>
                        </table>
                    </div>
                    <div id="infoDisplay" class="infoDisplay"></div>
                </div>
                <br />
                <div class="h2" id="dlDiv" style="height:1.85em;">
                    <table class="table2" style="display:inline-table;">
                        <tr>
                            <td>File name:&nbsp;&nbsp;<input type="text" class="textBox" id="fileName" onkeypress="enterKey(event,2)" style="width:8em;" />&nbsp;.&nbsp;</td>
                            <td>
                                <table class="table4" style="position:absolute;left:0;top:-1px;z-index:1;">
                                    <tr>
                                        <th onclick="tog(5,5)">
                                            <div id="header5" data-value="0" style="padding-left:0.2em;height:1.3em;width:2.7em;">pdf</div>
                                            <img src="downarrow.jpg" class="arrow" id="arrow5,5">
                                        </th>
                                    </tr>
                                    <tbody id="toggle5,5" style="display:none">
                                        <tr>
                                            <td id="td5,0" onclick="option(5,0)" onmouseover="highlight(5,0,0)" onmouseout="highlight(5,0,1)">
                                                <div id="option5,0" style="width:2.7em;padding-left:0.2em;height:1.3em;">pdf</div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td id="td5,1" onclick="option(5,1)" onmouseover="highlight(5,1,0)" onmouseout="highlight(5,1,1)">
                                                <div id="option5,1" style="width:2.7em;padding-left:0.2em;height:1.3em;">svg</div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td id="td5,2" onclick="option(5,2)" onmouseover="highlight(5,2,0)" onmouseout="highlight(5,2,1)">
                                                <div id="option5,2" style="width:2.7em;padding-left:0.2em;height:1.3em;">png</div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td id="td5,3" onclick="option(5,3)" onmouseover="highlight(5,3,0)" onmouseout="highlight(5,3,1)">
                                                <div id="option5,3" style="width:2.7em;padding-left:0.2em;height:1.3em;">jpg</div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td id="td5,4" onclick="option(5,4)" onmouseover="highlight(5,4,0)" onmouseout="highlight(5,4,1)">
                                                <div id="option5,4" style="width:2.7em;padding-left:0.2em;height:1.3em;">txt</div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td id="td5,5" onclick="option(5,5)" onmouseover="highlight(5,5,0)" onmouseout="highlight(5,5,1)">
                                                <div id="option5,5" style="width:2.7em;padding-left:0.2em;height:1.3em;">csv</div>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </td>
                        </tr>
                    </table>
                    <div class="button" onclick="download()">
                        <object class="icon" type="image/svg+xml" data="download.svg" style="width:1em;height:1.05em"></object>
                    </div>
                </div>
                <div class="toggle1" id="toggle0,5" style="display:none;height:1.7em;position:relative;">
                    <table class="table3">
                        <tr>
                            <td>
                                <div class="checkBox" id="checkBox5,0" onclick="check(5,0)">
                                    <object class="checkmark" type="image/svg+xml" data="check.svg"></object>
                                </div>
                            </td>
                            <td>Radius&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
                            <td>
                                <div class="checkBox" id="checkBox5,1" onclick="check(5,1)">
                                    <object class="checkmark" type="image/svg+xml" data="check.svg"></object>
                                </div>
                            </td>
                            <td>Center&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
                            <td><div class="checkBox" id="checkBox5,2" onclick="check(5,2)"></div></td>
                            <td>Curvature&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
                            <td><div class="checkBox" id="checkBox5,3" onclick="check(5,3)"></div></td>
                            <td>Curvature-center&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
                            <td><div class="checkBox" id="checkBox5,4" onclick="check(5,4)"></div></td>
                            <td>Ideal</td>
                        </tr>
                    </table>
                </div>

            </div>

        </div>
    </div>

    <script>

            var waitWrap = document.getElementById("waitWrap");
            setTimeout(function () {
                waitWrap.style.visibility = "visible";
            }, 1000);
            document.body.style.cursor = "auto";

            var circArray = [], reps = [], h, twoTor, d = 0, R = 20, scale, originX, originY, sqrt, two = 1, total = 0, scrollTop = 0, normInd = [], curvSet = initWidth = canvasWidth = 100, coords = [1, 0, 0, 1000], z = [0, 0];
            var visible = [], zoomPan = 0, maxWidth = 1700, downLoad = [1, 1, 0, 0, 0], styles = [], renderWidth = 2.5, maxR = 20, tor = [], prin = [], dets = [], infoCount = 0, infoArray = [], selectArray = [], selectCount = 0;
            var canvasContain = document.getElementById("canvasContain"), containLeft = canvasContain.offsetLeft, containTop = canvasContain.offsetTop, canvasTop = canvasLeft = (maxWidth - initWidth) / 2;
			var containWidth = canvasContain.offsetWidth, delta = initWidth / containWidth, selectLabelCount = 0;


            //continued fraction global variables
			var zX = zY = zD = startzX = startzY = startzD = 0; reducers = [], currentPrin = 1, cfElements = [], detList = [], detChoice = -1, ball = [], smallest9 = [], coverings = 0;

			var elementList = document.getElementById("elementList");
            var menu = document.getElementById("menus");
            var cayley = document.getElementById("cayley");
            var structure = document.getElementById("structure");
            var notes = document.getElementById("notes");
            var NS = "http://www.w3.org/2000/svg";
            var canvas = document.getElementById("canvas");
            var arrangement = document.getElementById("arrangement");
            var covering = document.getElementById("covering");
            var viewer = document.getElementById("viewer");
            canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
            canvasContain.addEventListener("mousedown", pan);
            canvas.addEventListener("mousewheel", zoom);
            canvas.addEventListener("DOMMouseScroll", zoom);
            canvas.addEventListener("dblclick", zoom);
            viewer.setAttribute("width", maxWidth);
            viewer.setAttribute("height", maxWidth);
            canvasContain.addEventListener("mouseenter", resetDisplay);
            canvasContain.addEventListener("mouseleave", resetHide);
            document.getElementById("colorPick").addEventListener("mousedown", colorPick);
			document.getElementById("background").setAttribute("width",maxWidth);
			document.getElementById("background").setAttribute("height",maxWidth);
            document.getElementById("curv").addEventListener("keydown", keyPress);
            document.getElementById("disc").addEventListener("keydown", keyPress);
            document.getElementById("curvUp").addEventListener("click", setCurv);
            document.getElementById("curvDown").addEventListener("click", setCurv);
            document.getElementById("curvWheel").addEventListener("mousewheel", setCurv);
            document.getElementById("curvWheel").addEventListener("DOMMouseScroll", setCurv);
            document.getElementById("draw").addEventListener("click", draw);
            window.addEventListener("resize", function () {
                containLeft = canvasContain.offsetLeft; containTop = canvasContain.offsetTop;
                containWidth = canvasContain.offsetWidth; delta = canvasWidth / containWidth;
            });

            var infoCircles = document.getElementById("infoCircles");
            var infoLabels = document.getElementById("infoLabels");
            var selectCircles = document.getElementById("selectCircles");
            var selectLabels = document.getElementById("selectLabels");

            var curvWheel = document.getElementById("curvWheel");
            var detWheel = document.createElement("td");
            detWheel.addEventListener("click",nextDet);
            detWheel.style.height = "1.4em"
            detWheel.style.width = "3.5em";

            var mouseDown = 0, infoCheck = 0;
            document.addEventListener("mousedown", function () { mouseDown = 1; }, true);
            document.addEventListener("mouseup", function () { mouseDown = 0; }, true);

            var stdDevHL = document.getElementById("stdDevHL");
            var blur = document.getElementById("blur");
            var stroke = document.getElementById("stroke");
            var demo = document.getElementById("demo");

			var col = [];
			col.push([49,15,153]);
			col[0] = [0,0,0];
			col.push([244,166,24]);
			col[1] = [0,0,0];
			col.push([232,0,23]);
			col[2] = [0,0,0];
			col.push([241,107,8]);
			col.push([119,5,152]);
			col.push([5,120,15]);
			col.push([7,166,208]);
			col.push([152,156,197]);
			col.push([169,91,76]);
			col.push([227,61,128]);
			col.push([0,200,100]);
			col.push([10, 52, 129]);


			var zDiv = document.createElement("div");
			zDiv.style.paddingBottom = "0.5em";
			var div = document.createElement("div");
			div.style.paddingBottom = "0.4em";
			div.innerHTML = "Click the determinants at the bottom of the canvas to see each arrangement. Adjust radii below.";
			zDiv.appendChild(div);
			var table = document.createElement("table");
			table.style.width = "100%";
			var gcdRow = document.createElement("tr");
			var cell = document.createElement("td");
			cell.style.verticAlign = "middle";
			cell.style.textAlign = "left";
			cell.style.height = "2em";
			cell.style.width = "9em";
			cell.innerHTML = "Admissible GCDs:";
			gcdRow.appendChild(cell);
			table.appendChild(gcdRow);
			zDiv.appendChild(table);
            table = document.createElement("table");
			var row = document.createElement("tr");
			cell = document.createElement("td");
			cell.style.verticalAlign = "middle";
			cell.innerHTML = "&#x1d700;&nbsp;&nbsp;=";
			row.appendChild(cell);
			var epsilonCell = document.createElement("td");
			epsilonCell.style.paddingLeft = "0.3em";
			epsilonCell.innerHTML = "1";
			epsilonCell.style.verticalAlign = "middle";
			epsilonCell.style.textAlign = "left";
			epsilonCell.style.width = "5em";
			row.appendChild(epsilonCell);
			var epsilonContain = document.createElement("td");
			epsilonContain.style.verticalAlign = "middle";
			var epsilonBar = document.createElementNS(NS, "svg");
			epsilonBar.addEventListener("mousedown", epsilonPick);
			epsilonBar.setAttribute("preserveAspectRatio", "none");
			epsilonBar.setAttribute("viewBox", "0 0 240 20");
			epsilonBar.setAttribute("width", "24em");
			epsilonBar.setAttribute("height", "2em");
			var epsilonRect = document.createElementNS(NS, "rect");
			epsilonRect.setAttribute("height", "4");
			epsilonRect.setAttribute("width", "225");
			epsilonRect.setAttribute("x", "8");
			epsilonRect.setAttribute("y", "8");
			epsilonRect.setAttribute("ry", "2");
			epsilonRect.setAttribute("rx", "2");
			epsilonRect.setAttribute("fill", "gray");
			epsilonRect.setAttribute("stroke", "none");
			epsilonRect.style.pointerEvents = "none";
			epsilonBar.appendChild(epsilonRect);
			var epsilonCirc = document.createElementNS(NS, "circle");
			epsilonCirc.setAttribute("cx", "232");
			epsilonCirc.setAttribute("cy", "10");
			epsilonCirc.setAttribute("r", "4");
			epsilonCirc.setAttribute("stroke", "black");
			epsilonCirc.setAttribute("fill", "rgba(4,38,230,0.5)");
			epsilonCirc.setAttribute("stroke-width", "0.5");
			epsilonBar.appendChild(epsilonCirc);
			epsilonContain.appendChild(epsilonBar);
			row.appendChild(epsilonContain); table.appendChild(row);
			zDiv.appendChild(table);
			div = document.createElement("div");
			div.style.paddingBottom = "0.4em";
			div.innerHTML = "To create continued fractions choose a norm with a principal determinant and a point in the plane.";
			zDiv.appendChild(div);
			table = document.createElement("table");
			table.style.margin = "0 auto";
			row = document.createElement("tr");
			cell = document.createElement("td");
			cell.innerHTML = "&#x1d467; =";
			cell.style.paddingRight = "0.2em";
			cell.style.paddingBottom = "1em";
			row.appendChild(cell);
			cell = document.createElement("td");
			cell.style.paddingBottom = "1em";
			cell.id = "z";
			cell.style.minWidth = "7.5em";
			row.appendChild(cell);
			table.appendChild(row);
			zDiv.appendChild(table);
			table = document.createElement("table");
			table.style.marginBottom = "0.5em";
			row = document.createElement("tr");
			cell = document.createElement("td");
			cell.style.verticalAlign = "middle";
			cell.style.width = "5em";
			cell.style.height = "2em";
			cell.style.textAlign = "left";
			cell.innerHTML = "Display:";
			row.appendChild(cell);
			var coefCell = document.createElement("td");
			coefCell.style.verticalAlign = "middle";
			coefCell.style.height = "2em";
			coefCell.style.width = "8em";
			coefCell.style.textAlign = "center";
			coefCell.style.border = "1px solid black";
			var span = document.createElement("span");
			span.style.pointerEvents = "none";
			span.innerHTML = "coefficients";
			coefCell.appendChild(span);
			coefCell.addEventListener("mousedown", switchDisplay);
			row.appendChild(coefCell);
			var conCell = document.createElement("td");
			conCell.style.verticalAlign = "middle";
			conCell.style.height = "2em";
			conCell.style.width = "8em";
			conCell.style.textAlign = "center";
			conCell.style.border = "none";
			span = document.createElement("span");
			span.style.pointerEvents = "none";
			span.innerHTML = "convergents";
			conCell.appendChild(span);
			conCell.addEventListener("mousedown", switchDisplay);
			row.appendChild(conCell);
			table.appendChild(row);
			zDiv.appendChild(table);
			var convergeTable = document.createElement("table");
			convergeTable.style.width = "100%";
			zDiv.appendChild(convergeTable);

			

			if(1 == 1){
				var dataArray = [[1,1,1,1,1,0,1,0,1,8,1,1,2,1,5,1,4,2,0,0],[2,1,1,1,1,0,1,0,1,8,1,1,3,1,2,2,8,2,0,0],[3,1,1,1,1,0,1,0,2,4,1,1,3,3,0,0]];
				dataArray.push([5,2,2,1,2,0,1,1,0,1,0,1,6,1,1,5,5,6,4,0,0,0,0,4,0,0,0]); dataArray.push([6,2,2,1,2,0,1,1,0,1,0,1,6,1,1,7,1,6,6,0,0,0,0,5,0,0,0]);			
				dataArray.push([7,1,1,1,1,0,1,0,2,6,1,1,2,3,7,7,3,2,2,2,0]); dataArray.push([10,2,2,1,2,0,1,1,0,1,0,1,6,1,1,11,1,10,10,3,3,-3,3,0,0,0,9,0,0,0]); 
				dataArray.push([11,1,1,1,1,0,1,0,2,6,1,1,3,5,5,4,3,2,-2,2,0]); dataArray.push([13,2,2,1,2,0,1,1,0,1,0,1,6,1,1,13,13,17,2,3,3,-3,3,0,0,0,12,0,0,0]); 
				dataArray.push([14,4,2,1,4,0,1,2,3,1,0,3,2,2,3,1,0,3,2,0,1,1,0,1,4,1,1,14,14,3,3,-3,3,0,1,0,13,4,2,10,7,7,0,4,2,2,2,20,0,1,1,0,0,0,0,1,1,0,0,0]);		
				dataArray.push([15,2,2,1,2,0,1,1,0,1,0,2,6,1,1,9,3,15,15,3,2,-2,2,0,0,0,8,0,0,0]);					
				dataArray.push([17,4,2,1,4,0,1,2,3,1,0,3,2,2,3,1,0,3,2,0,1,1,0,1,2,1,1,3,3,-3,3,0,1,0,16,2,2,11,0,4,2,2,2,22,0,1,1,0,0,0,0,1,1,0,0,0]);
				dataArray.push([19,1,1,1,1,0,1,0,2,14,1,1,74,6,24,9,5,9,6,5,7,8,11,7,6,2,-2,2,3,-3,3,0]);
				dataArray.push([21,4,4,2,2,2,0,1,2,3,1,0,3,2,2,3,0,1,3,2,1,0,1,0,1,2,1,1,0,0,0,0,8,0,0,0,0,0,13,0,0,0,0,0,20,0,0,0]);		
				dataArray.push([22,2,2,1,2,0,1,1,0,1,0,1,6,1,1,23,1,31,3,6,3,-3,3,5,-5,5,0,0,0,21,0,0,0]);												
				dataArray.push([23,3,1,1,3,0,1,2,1,2,0,2,0,1,1,0,2,8,1,1,12,14,8,10,23,23,6,2,-2,-2,3,-3,-3,0,1,2,21,4,-2,-5,-3,-7,3,2,3,12,4,2,-2,-2,10,-1,1,21,0,0,0]);
				dataArray.push([30,4,4,2,2,2,0,1,2,3,1,0,3,2,2,3,0,1,3,2,1,0,1,0,1,6,1,1,24,12,4,2,0,0,0,0,11,0,0,0,0,0,29,0,0,0,0,0,19,0,0,0]);				
				dataArray.push([39,4,2,1,4,0,1,2,3,1,0,3,2,2,3,1,0,3,2,0,1,1,0,2,6,1,1,9,3,39,39,3,2,-2,2,0,1,0,28,4,3,9,13,13,3,2,-5,7,4,2,-2,3,18,0,1,2,0,0,0,0,1,2,0,0,0]);
				dataArray.push([31,3,1,1,3,0,1,2,1,2,0,2,0,1,1,0,2,6,1,1,8,16,31,31,6,2,-2,-2,3,-3,3,0,1,2,29,6,-2,-8,-5,-6,-7,-10,6,2,5,17,2,7,18,4,2,-2,-2,16,-1,1,29,0,0,0]);
				dataArray.push([47,5,1,1,5,0,1,2,3,4,1,3,0,4,2,2,0,4,1,3,3,4,1,2,0,4,2,3,0,1,1,0,2,4,1,1,24,20,6,2,-2,-2,3,-3,-3,0,1,3,45,2,-3,-12,6,2,3,37,-2,-7,25,4,2,-2,-3,24,-1,4,45,0,0,0,1,2,2,4,2,7,7,17,0,4,2,2,-2,-14,-1,1,2,0,0,0]);			
				dataArray.push([43,1,1,1,1,0,1,0,2,22,1,1,11,21,13,20,17,19,23,18,31,17,6,7,10,15,14,10,15,12,21,8,9,2,-2,2,3,-3,3,5,-5,5,0]);
				dataArray.push([26,6,2,2,2,3,0,1,2,3,4,5,1,0,4,5,2,3,2,4,3,0,5,1,3,5,0,2,1,4,4,2,5,1,3,0,5,3,1,4,0,2,1,0,1,2,1,1,3,3,-3,-81,0,0,0,25,0,0,0,1,3,25,2,-3,-9,0,0,-1,2,25,0,0,0,0,3,1,0,0,0,0,2,1,0,0,0]);
				dataArray.push([29,6,2,2,2,3,0,1,2,3,4,5,1,0,4,5,2,3,2,4,5,0,3,1,3,5,0,4,1,2,4,2,3,1,5,0,5,3,1,2,0,4,1,0,1,2,1,1,3,3,-3,3,0,0,0,28,0,0,0,0,5,28,0,0,0,0,4,28,0,0,0,1,5,1,4,-5,-11,-13,-10,0,0,-1,4,1,0,0,0]);
				dataArray.push([34,4,2,1,4,0,1,2,3,1,0,3,2,2,3,1,0,3,2,0,1,1,0,1,2,1,1,6,3,-3,3,5,-5,5,0,1,0,33,6,2,28,17,17,19,11,0,8,2,2,2,56,2,3,-3,84,0,1,1,0,0,0,0,1,1,0,0,0]);
				dataArray.push([35,2,2,1,2,0,1,1,0,1,0,2,4,1,1,11,9,6,2,-2,2,3,-3,3,0,0,0,23,0,0,0]);
				dataArray.push([55,4,2,1,4,0,1,2,3,1,0,3,2,2,3,1,0,3,2,0,1,1,0,2,2,1,1,6,2,-2,2,3,-3,3,0,1,0,42,4,5,15,11,11,3,2,-7,17,4,2,-2,5,30,0,1,2,0,0,0,0,1,2,0,0,0]);
				dataArray.push([53,6,2,2,2,3,0,1,2,3,4,5,1,0,4,5,2,3,2,4,5,0,3,1,3,5,0,4,1,2,4,2,3,1,5,0,5,3,1,2,0,4,1,0,1,2,1,1,6,3,-3,3,5,-5,5,0,0,0,52,0,0,0,0,5,52,0,0,0,0,4,52,0,0,0,1,5,1,4,-13,-15,-17,-21,0,0,-1,4,1,0,0,0]);	
				dataArray.push([51,2,2,1,2,0,1,1,0,1,0,2,6,1,1,13,8,19,11,6,2,-2,2,5,-5,5,0,0,0,19,0,0,0]);			
			}												

			
			for (var i = 0; i < 5; i++) { document.getElementById("rgb" + i.toString()).addEventListener("keydown", keyPress); }

			for(var i = 2; i < 4; i++){
				var array = [3,5];
				for(var j = 0; j < array[i - 2]; j++){
					var checkBox = document.getElementById("checkBox" + i.toString() + "," + j.toString());
					if((i == 2 && j == 0) || (i == 3 && j == 2)){ checkBox.innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>"; }
					else{ checkBox.innerHTML = ""; }
				}
			}

			var primes = [];
			for (var i = 2; i < 5000; i++) {
			    var j = primes.length - 1;
			    while (j >= 0) {
			        if (i % primes[j] == 0) { break; }
			        j--;
			    }
			    if (j == -1) { primes.push(i); }
			}

			function artsy(){

			}

			function counterEx() {
			    var centX = originX + 3 * scale / 25, centY = originY - 14 * scale * Math.sqrt(31) / 25;
			    canvasWidth = 4 * scale * 0.0055263;
			    canvasLeft = centX - canvasWidth / 2;
			    canvasTop = centY - canvasWidth / 2;
			    delta = canvasWidth / containWidth;
			    canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			    for (var i = 0; i < total; i++) { render(i); }
			}

			function epsilonPick(e) {
			    var e = window.event || e; ++zoomPan;
			    var svgLeft = zDiv.offsetLeft + epsilonContain.offsetLeft, ratio = epsilonContain.offsetWidth;
			    ratio = 240 / ratio; var x = Math.max(9, Math.min(232, (e.clientX - svgLeft) * ratio));
			    epsilonCirc.setAttribute("cx", x.toString());
			    var epsilon = (x - 9) / 223;
			    epsilonCell.innerHTML = String(+epsilon.toFixed(3));
			    var cover = document.getElementById("cover" + detChoice.toString());
			    for (var i = cover.childNodes.length - 1; i >= 0; i--) {
			        var element = cover.childNodes[i];
			        element.setAttribute("r", String(epsilon * parseFloat(element.getAttribute("data-value"))));
			    }

			    epsilonBar.addEventListener("mousemove", dragCirc);
			    document.addEventListener("mouseup", stopCirc);

			    function dragCirc(e) {
			        var e = window.event || e;
			        x = Math.max(9, Math.min(232, (e.clientX - svgLeft) * ratio));
			        epsilonCirc.setAttribute("cx", x.toString());
			        epsilon = (x - 9) / 223;
			        epsilonCell.innerHTML = String(+epsilon.toFixed(3));
			        for (var i = cover.childNodes.length - 1; i >= 0; i--) {
			            var element = cover.childNodes[i];
			            element.setAttribute("r", String(epsilon * parseFloat(element.getAttribute("data-value"))));
			        }
			    }

			    function stopCirc() {
			        epsilonBar.removeEventListener("mousemove", dragCirc);
			        document.removeEventListener("mouseup", stopCirc);
			        delay(zoomPan);
			    }

			    function delay(count) {
			        setTimeout(function () {
			            if (count == zoomPan) {
			                document.body.classList.add("wait"); waitWrap.classList.add("disable");
			                setTimeout(function () {
			                    for (var i = 0; i < detList.length; i++) {
			                        var cover = document.getElementById("cover" + i.toString());
			                        for (var j = cover.childNodes.length - 1; j >= 0; j--) {
			                            var element = cover.childNodes[j];
			                            element.setAttribute("r", String(epsilon * parseFloat(element.getAttribute("data-value"))));
			                        }
			                    }
			                    setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
			                }, 10);
			            }
			        }, 200);
			    }
			}

			function switchDisplay(e) {
			    var e = window.event || e, target = e.target;
			    if (target == conCell) {
			        if (conCell.style.border == "none") {
			            conCell.style.border = "1px solid black";
			            coefCell.style.border = "none";
			            coverings = 0;
			            for (var i = 0; i < total; i++) { if (cfElements.indexOf(i) == -1) { visible[i] = 0; } }
			            var addWheel = document.getElementById("addWheel");
			            addWheel.removeChild(detWheel);
			            addWheel.appendChild(curvWheel);
			            while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }
			            while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			            while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			            selectLabelCount = 0;
			            infoArray = [];
			            var i = 0;
			            while (infoCount > 0) {
			                var element = canvas.childNodes[i];
			                if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			                else { i++; }
			            }
			            while (infoLabels.lastChild) { infoLabels.removeChild(infoLabels.lastChild); }
			            if (sqrt * 2 < two * (two + 1)) {
			                canvasWidth = scale * (two + 1) / 2;
			                originX = (maxWidth - canvasWidth) / 2; originY = maxWidth / 2 + scale * sqrt / (2 * two);
			            }
			            else {
			                canvasWidth = scale * sqrt / two;
			                originX = maxWidth / 2 - scale * (two + 1) / 4; originY = (maxWidth + canvasWidth) / 2;
			            }
			            initWidth = canvasWidth; canvasLeft = canvasTop = (maxWidth - canvasWidth) / 2; delta = canvasWidth / containWidth;
			            canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			            for (var i = 0; i < cfElements.length; i++) { render(cfElements[i]); }
			            if (startzD != 0) {
			                setTimeout(function () {
			                    zX = startzX; zY = startzY; zD = startzD;
			                    cfExpand();
			                }, 10);
			            }
			        }
			    }
			    else {
			        if (coefCell.style.border == "none") {
			            coefCell.style.border = "1px solid black";
			            conCell.style.border = "none";
			            coverings = 1;
			            var addWheel = document.getElementById("addWheel");
			            addWheel.removeChild(curvWheel);
			            addWheel.appendChild(detWheel);
			            while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }
			            while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			            while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			            selectLabelCount = 0;
			            var i = 0;
			            while (infoCount > 0) {
			                var element = canvas.childNodes[i];
			                if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			                else { i++; }
			            }
			            while (infoLabels.lastChild) { infoLabels.removeChild(infoLabels.lastChild); }
			            startingCover();
			            if (startzD != 0) {
			                setTimeout(function () {
			                    zX = startzX; zY = startzY; zD = startzD;
			                    cfExpand();
			                }, 10);
			            }
			        }
			    }
			}

			function resetDisplay() {
			    document.getElementById("curvContain").style.display = "block";
			    if (document.body.offsetHeight > window.innerHeight) {
			        var HTML = document.body.parentNode; if (scrollTop == 0) { scrollTop = parseInt(HTML.scrollTop); }
			        HTML.classList.add("noscroll"); HTML.style.top = String(-1 * scrollTop) + "px";
			    }
			}

			function resetHide() {
			    document.body.parentNode.classList.remove("noscroll"); window.scrollTo(0, scrollTop);
			    document.getElementById("curvContain").style.display = "none"; scrollTop = 0;
			}

			function detDisplay() {
			    document.getElementById("detContain").style.display = "block";
			    if (document.body.offsetHeight > window.innerHeight) {
			        var HTML = document.body.parentNode; if (scrollTop == 0) { scrollTop = parseInt(HTML.scrollTop); }
			        HTML.classList.add("noscroll"); HTML.style.top = String(-1 * scrollTop) + "px";
			    }
			}

			function detHide() {
			    document.body.parentNode.classList.remove("noscroll"); window.scrollTo(0, scrollTop);
			    document.getElementById("detContain").style.display = "none"; scrollTop = 0;
			}

			function posDisplay(e) {
                var e = window.event || e;
			    var x = (delta * Math.max(Math.min(e.clientX - containLeft, containWidth), 0) + canvasLeft - originX) / scale;
			    var y = (originY - delta * Math.max(Math.min(e.clientY - containTop, containWidth), 0) - canvasTop) / scale;
			    zY = Math.floor(two * 100 * y / sqrt + 0.5); zD = 100;
			    zX = two * Math.floor(100 * x + (zY % two) / two + 0.5) - zY % two;
			    y *= two / sqrt; x += (1 - two) * y / two;
			    x = +x.toFixed(2); y = +y.toFixed(2);
                document.getElementById("z").innerHTML = getEntry(x, y);
			}

			function posHide() {
			    if (startzD == 0) { document.getElementById("z").innerHTML = ""; }
			    else {
			        var y = startzY / startzD, x = (startzX / startzD + (1 - two) * y) / two;
			        x = +x.toFixed(2); y = +y.toFixed(2);
			        document.getElementById("z").innerHTML = getEntry(x, y);;
			    }
			}

			function nextDet() {
			    
			    var oldDet = detChoice, epsilon = parseFloat(epsilonCell.innerHTML);
			    while (detChoice == oldDet) {
			        detChoice++;
			        if (detChoice >= detList.length) { detChoice = 0; }
			        if (detChoice == oldDet) { break; }
			    }
			    if (detChoice != oldDet) {
			        if (1 == 0) {
			            detWheel.innerHTML = "";
			            var a = detList[detChoice][1], b = detList[detChoice][2]; a = (a + (1 - two) * b) / two;
			            if (detList[detChoice][0] == 1) { detWheel.innerHTML = getEntry(a, b); }
			            else {
			                var gcd = getGcd(a, b);
			                if (gcd != 1) { detWheel.innerHTML = gcd.toString(); }
			                var split = currentPrin / (gcd * gcd);
			                for (var i = 2; i <= split; i++) {
			                    var check = 0;
			                    for (var j = 2; j < i; j++) {
			                        if (i % j == 0) { check = 1; break; }
			                    }
			                    if (check == 0) {
			                        var exp = 0;
			                        while (split % i == 0) { exp++; split /= i; }
			                        if (exp != 0) {
			                            detWheel.innerHTML += "&#x1d52d;<sub class='subScript'>" + i.toString() + "</sub>";
			                            if (exp != 1) { detWheel.innerHTML += "<sup class='superScript'>" + exp.toString() + "</sup>"; }
			                        }
			                    }
			                }
			            }
			        }
			        if (oldDet != detChoice) {
			            document.getElementById("cover" + oldDet.toString()).style.display = "none";
			            document.getElementById("cover" + detChoice.toString()).style.display = "block";
			        }
			    }
			}

			function describe(i){
			    var description = document.getElementById("describe" + i.toString());
			    if (description.style.display == "block") { description.style.display = "none"; }
			    else { description.style.display = "block"; }
			}

			function cFrac() {
			    startzX = 0; startzY = 0; startzD = 0;
			    var cFracButton = document.getElementById("cFrac");
			    if (String(cFracButton.classList).indexOf("stayActive") > -1) {
			        document.body.classList.add("wait"); waitWrap.classList.add("disable");
			        setTimeout(function () {
			            cFracButton.classList.remove("stayActive"); detChoice = -1;
			            while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }
			            while (notes.lastChild) { notes.removeChild(notes.lastChild); }
			            while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			            while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			            selectLabelCount = 0;
			            var i = 0; infoArray = [];
			            while (infoCount > 0) {
			                var element = canvas.childNodes[i];
			                if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			                else { i++; }
			            }
			            while (infoLabels.lastChild) { infoLabels.removeChild(infoLabels.lastChild); }
			            canvasContain.removeEventListener("mouseover", posDisplay);
			            canvasContain.removeEventListener("mouseleave", posHide);
			            canvas.removeEventListener("mouseup", cfExpand);
			            if (coverings == 1) {
			                var addWheel = document.getElementById("addWheel");
			                addWheel.removeChild(detWheel);
			                addWheel.appendChild(curvWheel);
			            }
			            conCell.style.border = "none";
			            coefCell.style.border = "1px solid black";
			            coverings = 0;
			            maxWidth = 1700; initWidth = 100;
			            reset();
			            if (sqrt * 2 < two * (two + 1)) {
			                originX = (maxWidth - initWidth) / 2; originY = maxWidth / 2 + scale * sqrt / (2 * two);
			            }
			            else { originX = maxWidth / 2 - scale * (two + 1) / 4; originY = (maxWidth + initWidth) / 2; }
                        for (var i = 0; i < h; ++i) {
			                var ii = reps[i][0][1], cayleyText = document.getElementById("cayleyText" + i.toString() + ".0");
			                if (reps[ii][0][0] == -1) { ii -= 1; }
			                if (cayleyText.style.display == "none" && visible[i] == 1) { collapse(i); }
                        }
			            setTimeout(function () {
			                for (var i = 0; i < total; i++) { render(i); }
			                setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
			            }, 10);
			        }, 10);
			    }
			    else {
			        document.body.classList.add("wait"); waitWrap.classList.add("disable");
			        setTimeout(function () {
			            if (String(document.getElementById("info").classList).indexOf("stayActive") > -1) { info(); }
			            cFracButton.classList.add("stayActive");
			            while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			            selectLabelCount = 0;
			            var addWheel = document.getElementById("addWheel");
			            addWheel.removeChild(curvWheel);
			            addWheel.appendChild(detWheel);
			            detChoice = 0; coverings = 1;
                        //get some arrangement
			            var i = -1, done = []; cfElements = [];
			            for (var j = 0; j < h; j++) {
			                var jj = reps[j][0][1];
			                if (reps[jj][0][0] == -1) { jj--; }
			                if (i < 0) {
			                    if (document.getElementById("checkBox1," + jj.toString()).innerHTML != "") { i = jj; cfElements.push(j); }
			                }
			                else {
			                    if (jj == i) { cfElements.push(j); }
			                    else {
			                        if (done.indexOf(jj) == -1 && document.getElementById("checkBox1," + jj.toString()).innerHTML != "") {
			                            check(1, jj); done.push(jj);
			                        }
			                    }
			                }
			            }
			            if (i != -1) {
			                currentPrin = prin[cfElements[0]];
			                setTimeout(function () {
			                    startingCover();
			                    setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
			                }, 10);
			            }
			        }, 10);
			    }
			}

			function startingCover() {

			    converge = 0; detChoice = 0;
			    detList = []; reducers = []; ball = []; smallest9 = [];
			    startzD = 0;

                //rest epsilon
			    epsilonCell.innerHTML = "1";
			    epsilonCirc.setAttribute("cx", "232");

                //get determinants
			    var prime = 1, classes = [];
			    while (prime <= currentPrin * 20) {
			        if (prime == 1 || currentPrin % prime != 0) {
			            var check = 0;
			            for (var i = 2; i < prime; i++) { if (prime % i == 0) { check = 1; break; } }
			            if (check == 0) {
			                for (var i = 0; i < classes.length; i++) {
			                    if (principalCheck(classes[i][0], prime)) { check = 1; break; }
			                }
			                if (check == 0) {
			                    var i = -1;
			                    if (principalCheck(prime, prime)) { i = 1; }
			                    classes.push([prime, i]);
			                }
			            }
			        }
			        prime++;
			    }
                function principalCheck(i,j) {
			        var norm = two * two * i * j, maxY = Math.floor(Math.sqrt(norm / d));
			        for (var y = 0; y <= maxY; y++) {
			            if (i == 1 || y % i != 0) {
			                var maxX = Math.floor(Math.sqrt(norm - y * y * d) + 0.1);
			                for (var x = y % two; x <= maxX; x += two) {
			                    if (x * x + y * y * d == norm) {
			                        return true;
			                    }
			                }
			            }
			        }
			        return false;
			    }
                for (var i = 0; i < classes.length; i++) {
			        var prime = classes[i][0], norm = two * two * prime * currentPrin, maxY = Math.floor(Math.sqrt(norm / d));
			        for (var y = 0; y <= maxY; y++) {
			            if (prime == 1 || y % prime != 0) {
			                var maxX = Math.floor(Math.sqrt(norm - y * y * d) + 0.1);
			                for (var x = y % two; x <= maxX; x += two) {
			                    if (x * x + y * y * d == norm) {
			                        var check = 0;
			                        for (var j = 0; j < detList.length; j++) {
			                            if (detList[j][0] == prime) {
			                                var xx = (x * detList[j][1] + d * y * detList[j][2]) / two;
			                                var yy = (x * detList[j][2] - y * detList[j][1]) / two;
			                                xx = (xx + (1 - two) * yy) / two;
			                                if (xx % currentPrin == 0 && yy % currentPrin == 0) { detList.push([prime, x, y]); check = 1; }
			                                else { detList.push([-1 * prime, x, y]); check = -1; }
                                            break;
			                            }
			                        }
			                        if (check == 0) {
			                            detList.push([prime, x, y]);
			                            if (y != 0) { detList.push([classes[i][1] * prime, x, -1 * y]); }
			                        }
			                        else {
			                            if (y != 0) { detList.push([check * classes[i][1] * prime, x, -1 * y]); }
			                        }
			                    }
			                }
			            }
			        }
			    }


			    //get ball
                var boundN = Math.ceil(Math.sqrt(currentPrin) + Math.sqrt(two * two + d / (two * two)) / 2);
                boundN *= boundN; ball.push([0, 0]);
			    for(var N = 1; N <= boundN; N++){
			        var maxY = Math.floor(Math.sqrt(two * two * currentPrin / d) + 0.01);
			        for (var y = 0; y <= maxY; y++) {
			            var x = Math.floor(Math.sqrt(two * two * N - d * y * y) + 0.5);
			            if (x * x + d * y * y == two * two * N) {
			                ball.push([x, y]);
			                if (y != 0) {
			                    ball.push([x, -1 * y]);
			                    if (x != 0) {
			                        ball.push([1 * x, y]);
			                        ball.push([-1 * x, -1 * y]);
			                    }
			                }
			                else {
			                    if (x != 0) { ball.push([-1 * x, y]); }
			                }
			            }
			        }
			    }


			    //get smallest 9 for each determinant
			    var N = 1, check = 0;
			    for (var i = 0; i < detList.length; i++) { smallest9.push([[0, 0]]); }
			    while (check == 0) {
			        var maxY = Math.floor(Math.sqrt(two * two * N * currentPrin / d) + 0.01);
			        for (var y = -1 * maxY; y <= maxY; y++) {
			            var x = Math.floor(Math.sqrt(two * two * N * currentPrin - d * y * y) + 0.5);
			            if (x * x + d * y * y == two * two * N * currentPrin) {
			                for (var i = 0; i < detList.length; i++) {
			                    if (smallest9[i].length < 9) {
			                        var R = (x * detList[i][1] + d * y * detList[i][2]) / two;
			                        var I = (y * detList[i][1] - x * detList[i][2]) / two;
			                        R = (R + (1 - two) * I) / two;
			                        if (R % currentPrin == 0 && I % currentPrin == 0) {
			                            smallest9[i].push([x, y]);
			                            if (x != 0) { smallest9[i].push([-1 * x, -1 * y]); }
			                        }
			                    }
			                }
			            }
			        }
			        check = 1; N++;
			        for (var i = 0; i < smallest9.length; i++) { if (smallest9[i].length < 9) { check = 0; break; } }
			    }


			    //get good window size
			    if (detList[0][0] == 1) { var detX = detList[0][1], detY = detList[0][2]; }
			    else { var detX = two * Math.sqrt(currentPrin), detY = 0; }
			    var maxR = 0, maxI = 0;
			    for (var i = 0; i < smallest9.length; i++) {
			        for (var j = 0; j < 9; j++) {
			            var x = smallest9[i][j][0], y = smallest9[i][j][1];
			            var R = (x * detX + d * y * detY) / (currentPrin * two * two);
			            var I = sqrt * (y * detX - x * detY) / (currentPrin * two * two);
			            if (Math.abs(R) > maxR) { maxR = Math.abs(R); }
			            if (Math.abs(I) > maxI) { maxI = Math.abs(I); }
			        }
			    }
			    canvasWidth = scale * 2 * (Math.max(maxR, maxI) + 1);
			    initWidth = canvasWidth;
			    maxWidth = 2 * (canvasWidth - scale);
			    canvasLeft = (maxWidth - canvasWidth) / 2; canvasTop = (maxWidth - canvasWidth) / 2;
			    originX = maxWidth / 2; originY = maxWidth / 2;
			    delta = canvasWidth / containWidth;
			    canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			    var boundWidth = Math.sqrt(2) * (canvasWidth - scale);


			    //get reducers
			    var tempPrin = currentPrin;
			    if (tempPrin % 2 == 0) {
			        if ((d - 7) % 8 == 0) { getGenerator(2); }
			        else { reducers.push([two * 2, 0]); }
			        while(tempPrin % 2 == 0){ tempPrin /= 2; }
			    }
			    var prime = 3;
			    while(prime <= tempPrin) {
			        if (tempPrin % prime == 0) {
			            var check = 0;
			            for (var i = Math.floor(Math.sqrt(prime) + 0.1); i > 1; i--) {
			                if (prime % i == 0) { check = 1; break; }
			            }
			            if (check == 0) {
			                if (d % prime == 0) { reducers.push([two * prime, 0]); }
			                else {
			                    for (var j = (prime - 1) / 2; j >= 0; j++) {
			                        if ((j * j + d) % prime == 0) { check = 1; break; }
			                    }
			                    if (check == 0) { reducers.push([two * prime, 0]); }
			                    else { getGenerator(prime); }
			                }
			                while (tempPrin % prime == 0) { tempPrin /= prime; }
			            }
			        }
			        prime++;
			    }
			    function getGenerator(base) {
			        var N = base, check = 0;
			        while (check == 0) {
			            N *= base;
			            var maxY = Math.floor(Math.sqrt(two * two * N / d) + 0.01);
			            for (var y = 1; y <= maxY; y++) {
			                var x = Math.floor(Math.sqrt(two * two * N - d * y * y) + 0.5);
			                if (x * x + d * y * y == two * two * N) {
			                    reducers.push([x, y]); reducers.push([x, -1 * y]);
			                    check = 1; break;
			                }
			            }
			        }
			    }


			    //get possible coverings
			    while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }

			    for (var i = 0; i < detList.length; i++) {
			        var cover = document.createElementNS(NS, "g");
			        cover.id = "cover" + i.toString();
			        cover.style.display = "none";
			        arrangement.appendChild(cover);
			        if (i == 0) { var color = "rgba(4,38,210,0.5)"; }
			        else { var color = "rgba(49,157,101,0.5)"; }
			        var prime = detList[i][0], iX = detList[i][1], iY = detList[i][2];
			        if (detList[0][0] == 1) { var detX = detList[0][1], detY = detList[0][2], denom = currentPrin; }
			        else { var detX = two * currentPrin, detY = 0, denom = Math.sqrt(currentPrin); }

			        if (i == -1) {
			            var realZ = [-3.27688, 0.956802 + 0.5, -2.96988, -4.49638, -5.16105, 1.51181, 3.19346];
			            var imZ = [11.4759, -2.04232 + 3.4278, 5.17751, 2.33248, -1.79553, -1.5537, 2.9749];
			            var imA = [12, 48, -12, 12, 18, -12];
			            var realA = [12, -96, -12, -84, -126, - 108];
			            var rads = [12, 6, 12, 4, 6, 4];
			            var zList = [0, 3, 4, 8, 11, 15, 16];
			        }
			        if (i == -1) {
			            var realZ = [0.286031, 0.103297, -3.00939, -4.32855, -5.5];
			            var imZ = [5.85768, 2.65118, 2.63678, -5.24503, -4.0];
			            var imA = [24, 12, 12, -12, -12];
			            var realA = [24, 12, -60, -132, -108];
			            var rads = [4, 2, 2, 6, 2];
			            var zList = [1, 2, 5, 7, 14];
			        }
			        if (i == -1) {
			            var realZ = [0.849139, -5.81775, 3.4842, -4.85259 + 0.25, -4.53546];
			            var imZ = [1.78722, -1.99831, 1.85692, 2.10525 - 0.1, -4.43483];
			            var imA = [12, -12, 12, 12, -12];
			            var realA = [60, -204, 108, -84, -60];
			            var rads = [6, 12, 4, 12, 6];
			            var zList = [6, 9, 10, 12, 13];
			        }
			        if (1 == 0) {
			            var realZ = [101 / 50, 25 / 608, -279 / 282, -69 / 136];
			            var imZ = [9 * sqrt / 50, -225 * sqrt / 608, -79 * sqrt / 282, -31 * sqrt / 136];
			            var imA = [0, -1 * sqrt / 2, -1 * sqrt / 2];
			            var realA = [2, 1 / 2, -1 / 2];
			            var rads = [1, 1, 1];
			            var zList = [0, 1, 2, 3];
			        }
			        if (1 == 0) {
			            var realZ = [28 / 53, -25 / 13, 1 / 2, -1];
			            var imZ = [8 * sqrt / 53, -8 * sqrt / 13, -5 * sqrt / 2, sqrt];
			            var imA = [0, -1 * sqrt, -2 * sqrt, sqrt];
			            var realA = [1, -2, 1, -1];
			            var rads = [1, 1, 1, 1];
			            var zList = [0, 1, 2, 3];
			        }


			       
                    

			        var maxY = Math.floor(two * denom * boundWidth / (scale * sqrt));
			        var maxX = Math.floor(two * denom * boundWidth / scale);
			        for (var l = currentPrin; l > 0; l--) {
			            for (var y = -1 * maxY; y <= maxY; y++) {
			                for (var x = -1 * maxX + Math.abs((maxX + y) % two) ; x <= maxX; x += two) {
			                    var R = (x * detX - d * y * detY) / two;
			                    var I = (y * detX + x * detY) / two;
			                    var R = (R + (1 - two) * I) / two;
			                    if (R % currentPrin == 0 && I % currentPrin == 0) {
			                        R /= currentPrin; I /= currentPrin; R = two * R + (two - 1) * I;
			                        for (var j = i; j <= i; j++) {
			                            if (detList[j][0] != prime + 1000) {
			                                var check = 0, jX = detList[j][1], jY = detList[j][2];
			                                loop: for (var k = 0; k < Math.min(j, 1) ; k++) {
			                                    if (detList[k][0] == prime) {
			                                        var kX = detList[k][1], kY = detList[k][2];
			                                        var prodX = (jX * kX + d * jY * kY) / two;
			                                        var prodY = (jX * kY - jY * kX) / two;
			                                        var testX = (R * prodX - d * I * prodY) / two;
			                                        var testY = (I * prodX + R * prodY) / two;
			                                        testX = (testX + (1 - two) * testY) / two;
			                                        if (testX % currentPrin == 0 && testY % currentPrin == 0) {
			                                            check = 1; break loop;
			                                        }
			                                    }
			                                }
			                                if (check == 0) {
			                                    var gcd = getNormGcd(R, I, jX, jY);
			                                    if (gcd % prime == 0) { gcd /= Math.abs(prime); }
			                                    var prodX = (iX * jX + d * iY * jY) / (currentPrin * prime * two * two);
			                                    var prodY = (iY * jX - iX * jY) / (currentPrin * prime * two * two);
			                                    var centX = (x * prodX - d * y * prodY) / (denom * two);
			                                    var centY = sqrt * (x * prodY + y * prodX) / (denom * two);
			                                    if (gcd == l) {
			                                        var circle = document.createElementNS(NS, "circle");
			                                        circle.setAttribute("cy", String(originX + scale * centX));
			                                        circle.setAttribute("cx", String(originY + scale * centY));
			                                        circle.setAttribute("r", String(scale * Math.sqrt(gcd / currentPrin)));
			                                        if (x == -200 & y == 0) {
			                                            circle.setAttribute("r", String(scale * Math.sqrt(2 * gcd / currentPrin)));
			                                        }
			                                        circle.setAttribute("data-value", String(scale * Math.sqrt(gcd / currentPrin)));
			                                        circle.setAttribute("fill", "rgba(0,0,0,0.2)");
			                                        circle.setAttribute("stroke", "rgb(0,0,0)");
			                                        circle.setAttribute("stroke-width", String(canvasWidth / 2000));
			                                        cover.appendChild(circle);

			                                        if (l == 6 && i == -1) {
			                                            centX += 0.5;
			                                            circle = document.createElementNS(NS, "circle");
			                                            circle.setAttribute("cx", String(originX + scale * centX));
			                                            circle.setAttribute("cy", String(originY - scale * centY));
			                                            circle.setAttribute("r", String(scale * Math.sqrt(gcd / currentPrin)));
			                                            if (x == -200 & y == 0) {
			                                                circle.setAttribute("r", String(scale * Math.sqrt(2 * gcd / currentPrin)));
			                                            }
			                                            circle.setAttribute("data-value", String(scale * Math.sqrt(gcd / currentPrin)));
			                                            circle.setAttribute("fill", color);
			                                            circle.setAttribute("stroke", "rgb(0,0,0)");
			                                            circle.setAttribute("stroke-width", String(canvasWidth / 2000));
			                                            cover.appendChild(circle);
			                                        }
			                                    }
			                                    if (l == 0) {
			                                        if (gcd == 1) {
			                                            var gcdCheck = getNormGcd(R + 2, I, jX, jY);
			                                            if (gcdCheck % prime == 0) { gcdCheck /= Math.abs(prime); }
			                                            if (gcdCheck == 2) {
			                                                var path = document.createElementNS(NS, "path");
			                                                var dString = "M " + String(originX + scale * (centX + 0.125)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                                dString += " A " + String(scale / Math.sqrt(2)) + "," + String(scale / Math.sqrt(2)) + ",0,0,0," + String(originX + scale * (centX + 0.125)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                                path.setAttribute("d", dString);
			                                                path.setAttribute("stroke", "rgb(0,0,0)");
			                                                path.setAttribute("fill", "none");
			                                                path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                                cover.appendChild(path);
			                                                path = document.createElementNS(NS, "path");
			                                                dString = "M " + String(originX + scale * (centX + 0.125)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                                dString += " A " + String(scale / 3) + "," + String(scale / 3) + ",0,0,1," + String(originX + scale * (centX + 0.125)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                                path.setAttribute("d", dString);
			                                                path.setAttribute("stroke", "rgb(0,0,0)");
			                                                path.setAttribute("fill", "none");
			                                                path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                                cover.appendChild(path);
			                                            }
			                                            else {
			                                                var path = document.createElementNS(NS, "path");
			                                                var dString = "M " + String(originX + scale * (centX - 0.125)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                                dString += " A " + String(scale / 3) + "," + String(scale / 3) + ",0,0,0," + String(originX + scale * (centX - 0.125)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                                path.setAttribute("d", dString);
			                                                path.setAttribute("stroke", "rgb(0,0,0)");
			                                                path.setAttribute("fill", "none");
			                                                path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                                cover.appendChild(path);
			                                                path = document.createElementNS(NS, "path");
			                                                dString = "M " + String(originX + scale * (centX - 0.125)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                                dString += " A " + String(scale / Math.sqrt(2)) + "," + String(scale / Math.sqrt(2)) + ",0,0,1," + String(originX + scale * (centX - 0.125)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                                path.setAttribute("d", dString);
			                                                path.setAttribute("stroke", "rgb(0,0,0)");
			                                                path.setAttribute("fill", "none");
			                                                path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                                cover.appendChild(path);
			                                            }
			                                        }
			                                        if (gcd == 4) {
			                                            var path = document.createElementNS(NS, "path");
			                                            var dString = "M " + String(originX + scale * (centX - 0.625)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                            dString += " A " + String(scale * Math.sqrt(2)) + "," + String(scale * Math.sqrt(2)) + ",0,0,1," + String(originX + scale * (centX + (Math.sqrt(115) - 19) / 12)) + "," + String(originY - scale * (centY - 0.5 * (5 * (Math.sqrt(115) - 19) / 6 + 12) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            path = document.createElementNS(NS, "path");
			                                            dString = "M " + String(originX + scale * (centX + 0.625)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                            dString += " A " + String(scale * Math.sqrt(2)) + "," + String(scale * Math.sqrt(2)) + ",0,0,1," + String(originX + scale * (centX - (Math.sqrt(115) - 19) / 12)) + "," + String(originY - scale * (centY + 0.5 * (5 * (Math.sqrt(115) - 19) / 6 + 12) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);

			                                            path = document.createElementNS(NS, "path");
			                                            dString = "M " + String(originX + scale * (centX - 0.625)) + "," + String(originY - scale * (centY + Math.sqrt(7) / 8));
			                                            dString += " A " + String(scale * Math.sqrt(2)) + "," + String(scale * Math.sqrt(2)) + ",0,0,0," + String(originX + scale * (centX + (Math.sqrt(345) - 29) / 16)) + "," + String(originY - scale * (centY + 0.5 * (3 * (Math.sqrt(345) - 29) / 8 + 8) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            path = document.createElementNS(NS, "path");
			                                            dString = "M " + String(originX + scale * (centX + 0.625)) + "," + String(originY - scale * (centY - Math.sqrt(7) / 8));
			                                            dString += " A " + String(scale * Math.sqrt(2)) + "," + String(scale * Math.sqrt(2)) + ",0,0,0," + String(originX + scale * (centX - (Math.sqrt(345) - 29) / 16)) + "," + String(originY - scale * (centY - 0.5 * (3 * (Math.sqrt(345) - 29) / 8 + 8) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);

			                                            path = document.createElementNS(NS, "path");
			                                            dString = "M " + String(originX + scale * (centX + (Math.sqrt(1380) - 34) / 32)) + "," + String(originY - scale * (centY + 0.5 * (3 * (Math.sqrt(1380) - 34) / 16 - 8) / sqrt));
			                                            dString += " A " + String(scale * Math.sqrt(3)) + "," + String(scale * Math.sqrt(3)) + ",0,0,0," + String(originX + scale * (centX - (Math.sqrt(115) - 4) / 12)) + "," + String(originY - scale * (centY + 0.5 * (5 * (Math.sqrt(115) - 4) / 6 - 12) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            path = document.createElementNS(NS, "path");
			                                            dString = "M " + String(originX + scale * (centX - (Math.sqrt(1380) - 34) / 32)) + "," + String(originY - scale * (centY - 0.5 * (3 * (Math.sqrt(1380) - 34) / 16 - 8) / sqrt));
			                                            dString += " A " + String(scale * Math.sqrt(3)) + "," + String(scale * Math.sqrt(3)) + ",0,0,0," + String(originX + scale * (centX + (Math.sqrt(115) - 4) / 12)) + "," + String(originY - scale * (centY - 0.5 * (5 * (Math.sqrt(115) - 4) / 6 - 12) / sqrt));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);

			                                            var line = document.createElementNS(NS, "line");
			                                            line.setAttribute("x1", String(originX + scale * (centX - (Math.sqrt(1380) - 34) / 32)));
			                                            line.setAttribute("y1", String(originY - scale * (centY - 0.5 * (3 * (Math.sqrt(1380) - 34) / 16 - 8) / sqrt)));
			                                            line.setAttribute("x2", String(originX + scale * (centX + (Math.sqrt(345) - 29) / 16)));
			                                            line.setAttribute("y2", String(originY - scale * (centY + 0.5 * (3 * (Math.sqrt(345) - 29) / 8 + 8) / sqrt)));
			                                            line.setAttribute("stroke", "rgb(0,0,0)");
			                                            line.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(line);
			                                            line = document.createElementNS(NS, "line");
			                                            line.setAttribute("x1", String(originX + scale * (centX + (Math.sqrt(115) - 4) / 12)));
			                                            line.setAttribute("y1", String(originY - scale * (centY - 0.5 * (5 * (Math.sqrt(115) - 4) / 6 - 12) / sqrt)));
			                                            line.setAttribute("x2", String(originX + scale * (centX - (Math.sqrt(115) - 19) / 12)));
			                                            line.setAttribute("y2", String(originY - scale * (centY + 0.5 * (5 * (Math.sqrt(115) - 19) / 6 + 12) / sqrt)));
			                                            line.setAttribute("stroke", "rgb(0,0,0)");
			                                            line.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(line);
			                                        }
			                                    }
			                                    if (l == -1) {
			                                        if (gcd == 1) {
			                                            var path = document.createElementNS(NS, "path");
			                                            var dString = "M " + String(originX + scale * centX) + "," + String(originY - scale * (centY - 0.5 / Math.sqrt(3)));
			                                            dString += " A " + String(scale / 3) + "," + String(scale / 3) + ",0,0,0," + String(originX + scale * centX) + "," + String(originY - scale * (centY + 0.5 / Math.sqrt(3)));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            path = document.createElementNS(NS, "path");
			                                            var dString = "M " + String(originX + scale * centX) + "," + String(originY - scale * (centY - 0.5 / Math.sqrt(3)));
			                                            dString += " A " + String(scale / 3) + "," + String(scale / 3) + ",0,0,1," + String(originX + scale * centX) + "," + String(originY - scale * (centY + 0.5 / Math.sqrt(3)));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            var line = document.createElementNS(NS, "line");
			                                            line.setAttribute("x1", String(originX + scale * centX));
			                                            line.setAttribute("y1", String(originY - scale * (centY - 0.5 / Math.sqrt(3))));
			                                            line.setAttribute("x2", String(originX + scale * centX));
			                                            line.setAttribute("y2", String(originY - scale * (centY - 0.5 * Math.sqrt(11))));
			                                            line.setAttribute("stroke", "rgb(0,0,0)");
			                                            line.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(line);
			                                            line = document.createElementNS(NS, "line");
			                                            line.setAttribute("x1", String(originX + scale * centX));
			                                            line.setAttribute("y1", String(originY - scale * (centY + 0.5 / Math.sqrt(3))));
			                                            line.setAttribute("x2", String(originX + scale * centX));
			                                            line.setAttribute("y2", String(originY - scale * (centY + 0.5 * Math.sqrt(11))));
			                                            line.setAttribute("stroke", "rgb(0,0,0)");
			                                            line.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(line);
			                                        }
			                                        if (gcd == 4) {
			                                            var path = document.createElementNS(NS, "path");
			                                            var dString = "M " + String(originX + scale * centX) + "," + String(originY - scale * (centY + (sqrt - Math.sqrt(11)) / 2));
			                                            dString += " A " + String(scale * Math.sqrt(3)) + "," + String(scale * Math.sqrt(3)) + ",0,0,0," + String(originX + scale * (centX + 1)) + "," + String(originY - scale * (centY + (sqrt - Math.sqrt(11)) / 2));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                            path = document.createElementNS(NS, "path");
			                                            var dString = "M " + String(originX + scale * centX) + "," + String(originY - scale * (centY - (sqrt - Math.sqrt(11)) / 2));
			                                            dString += " A " + String(scale * Math.sqrt(3)) + "," + String(scale * Math.sqrt(3)) + ",0,0,1," + String(originX + scale * (centX + 1)) + "," + String(originY - scale * (centY - (sqrt - Math.sqrt(11)) / 2));
			                                            path.setAttribute("d", dString);
			                                            path.setAttribute("stroke", "rgb(0,0,0)");
			                                            path.setAttribute("fill", "none");
			                                            path.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                            cover.appendChild(path);
			                                        }
			                                    }
			                                    if (l == -1) {
			                                        var expand = 1;
			                                        if (gcd == 2) { expand = 1.01845103922; }
			                                        var circle = document.createElementNS(NS, "circle");
			                                        circle.setAttribute("cx", String(originX + scale * (x * prodX - d * y * prodY) / (denom * two)));
			                                        circle.setAttribute("cy", String(originY - scale * sqrt * (x * prodY + y * prodX) / (denom * two)));
			                                        circle.setAttribute("r", String(scale * expand * Math.sqrt(gcd / currentPrin)));
			                                        circle.setAttribute("data-value", String(scale * expand * Math.sqrt(gcd / currentPrin)));
			                                        circle.setAttribute("fill", "none");
			                                        circle.setAttribute("stroke", "rgb(0,0,0)");
			                                        circle.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                                        cover.appendChild(circle);
			                                    }
			                                }
			                            }
			                        }
			                    }
			                }
			            }
			        }
						
						//red dots
						for(var l = -5; l < -5; l++){
							var circle = document.createElementNS(NS, "circle");
			            circle.setAttribute("cy", String(originX + scale * (2*l+1)/4));
			            circle.setAttribute("cx", String(originY + scale * sqrt/4));
			            circle.setAttribute("r", String(scale * 0.04));
			            circle.setAttribute("data-value", String(scale * 0.045));
			            circle.setAttribute("fill", "rgb(255,255,255)");
			            circle.setAttribute("stroke", "rgb(0,0,0)");
			            circle.setAttribute("stroke-width", String(canvasWidth / 2000));
			            cover.appendChild(circle);
						}

			        if (1 == 0) {
			            var rectWidth = initWidth * Math.pow(0.9, 23);
			            var rectLeft = originX + scale * 1 / 2 - 0.99 * rectWidth / 2;
			            var rectTop = originY - scale * Math.sqrt(47 - 8 * sqrt) / 2 - rectWidth / 2;
			            var rect = document.createElementNS(NS, "rect");
			            rect.setAttribute("x", rectLeft);
			            rect.setAttribute("y", rectTop);
			            rect.setAttribute("width", 0.98 * rectWidth);
			            rect.setAttribute("height", rectWidth);
			            rect.setAttribute("fill", "none");
			            rect.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * 0.18)));
			            rect.setAttribute("stroke", "rgb(0,0,0)");
			            selectCircles.appendChild(rect); ++selectCount;
			            if (1 == 0) {
			                var circle = document.createElementNS(NS, "circle");
			                circle.setAttribute("cx", String(originX - scale * 101 / 100));
			                circle.setAttribute("cy", String(originY - scale * sqrt * 13 / 100));
			                circle.setAttribute("r", String(canvasWidth * 0.0065));
			                circle.setAttribute("fill", "rgb(0,0,0)");
			                circle.setAttribute("stroke", "none");
			                selectCircles.appendChild(circle);
			                ++selectCount;
			            }
			        }
			        if (i == -1) {
			            if (!document.getElementById("labels0") || 1 == 1) {
			                for (var k = 0; k < realZ.length; k++) {
			                    if (1 == 1) {
			                        var tempR = (realZ[k] + sqrt * imZ[k]) / 24;
			                        imZ[k] = (imZ[k] - realZ[k] * sqrt) / 24;
			                        realZ[k] = tempR;
			                    }
			                    var label = document.createElementNS(NS, "g");
			                    var rect = document.createElementNS(NS, "rect");
			                    rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			                    rect.setAttribute("x", String(-0.011 * initWidth));
			                    rect.setAttribute("y", String(-0.011 * initWidth));
			                    rect.setAttribute("width", String(0.022 * initWidth));
			                    rect.setAttribute("height", String(0.022 * initWidth));
			                    rect.setAttribute("rx", String(0.004 * initWidth));
			                    rect.setAttribute("ry", String(0.004 * initWidth));
			                    rect.setAttribute("stroke", "rgb(0,0,0)"); rect.setAttribute("fill", "rgb(255,255,255)");
			                    rect.setAttribute("stroke-width", String(0.0008 * initWidth));
			                    label.appendChild(rect);
			                    var text = document.createElementNS(NS, "text");
			                    text.setAttribute("font-size", String(0.02 * initWidth));
			                    text.setAttribute("fill", "rgb(0,0,0)");
			                    text.setAttribute("x", "0"); text.setAttribute("y", String(0.007 * initWidth));
			                    text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			                    text.style.pointerEvents = "none"; text.innerHTML = zList[k].toString();
			                    label.appendChild(text); selectLabels.appendChild(label);
			                    label.setAttribute("transform", "translate(" + String(originX + scale * realZ[k]) + "," + String(originY - scale * imZ[k]) + ") scale(" + String(canvasWidth / initWidth) + ")");

			                }
			                for (var k = 0; k < realA.length; k++) {
			                    if (1 == 1) {
			                        realA[k] /= 24; imA[k] *= sqrt / 24;
			                        var tempR = (realA[k] + sqrt * imA[k]) / 24;
			                        imA[k] = (imA[k] - realA[k] * sqrt) / 24;
			                        realA[k] = tempR;
			                    }
			                    var circle = document.createElementNS(NS, "circle");
			                    circle.setAttribute("cx", String(originX + scale * realA[k]));
			                    circle.setAttribute("cy", String(originY - scale * imA[k]));
			                    if (1 == 1) {
			                        circle.setAttribute("r", String(scale * Math.sqrt(rads[k] / 12)));
			                    }
			                    else { circle.setAttribute("r", String(scale * Math.sqrt(rads[k]))); }
			                    circle.setAttribute("fill", "rgba(149,94,186,1)"); circle.setAttribute("stroke", "rgb(0,0,0)");
			                    circle.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6])));
			                    selectCircles.appendChild(circle);
			                    var circle = document.createElementNS(NS, "circle");
			                    circle.setAttribute("cx", String(originX + scale * realA[k]));
			                    circle.setAttribute("cy", String(originY - scale * imA[k]));
			                    circle.setAttribute("r", String(canvasWidth * 0.0055));
			                    circle.setAttribute("fill", "rgb(0,0,0)"); circle.setAttribute("stroke", "none");
			                    selectCircles.appendChild(circle);
			                    selectArray.push([0, 0, 0, 0, 0, 0, 0.18, 1]);
			                    selectArray.push([0, 0, 0, 0, 0, 0, 0.18, 1]);
			                    ++selectCount; ++selectCount;
			                }
			            }
			        }
			    }

			    if (1 == 0) {
			        canvasWidth = scale * 5.2;
			        canvasLeft = originX - scale * 2.37;
			        canvasTop = originY - scale * 3.22;
			        delta = canvasWidth / containWidth;
			        canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			    }

                //display everything
			    detWheel.innerHTML = getEntry((detList[0][1] + (1 - two) * detList[0][2]) / two, detList[0][2]);
			    while (notes.lastChild) { notes.removeChild(notes.lastChild); }
			    while (convergeTable.lastChild) { convergeTable.removeChild(convergeTable.lastChild); }
			    while (1 < gcdRow.childNodes.length) { gcdRow.removeChild(gcdRow.lastChild); }
			    while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			    var i = 0;
			    while (infoCount > 0) {
			        var element = canvas.childNodes[i];
			        if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			        else { i++; }
			    }
			    notes.appendChild(zDiv);
			    for (var i = 1; i <= currentPrin; i++) {
			        if (currentPrin % i == 0) {
			            var cell = document.createElement("td");
			            cell.style.verticAlign = "middle";
			            cell.style.textAlign = "center";
			            cell.style.height = "2em";
			            cell.style.width = "1.4em";
			            var HTML = "<div class='checkBox' id='checkBox8," + i.toString() + "' onclick='check(8," + i.toString() + ")'>";
			            HTML += "<object class='checkmark' type='image/svg+xml' data='check.svg'></object></div>";
			            cell.innerHTML = HTML;
			            gcdRow.appendChild(cell);
			            cell = document.createElement("td");
			            cell.style.verticAlign = "middle";
			            cell.style.textAlign = "left";
			            cell.style.height = "2em";
			            cell.style.width = "2em";
			            cell.innerHTML = i.toString();
			            gcdRow.appendChild(cell);
			                cell = document.createElement("td");
			                cell.style.height = "2em";
			                gcdRow.appendChild(cell);
			        }
			    }
                if (detList[0][0] == 1) {
			        canvasContain.addEventListener("mousemove", posDisplay);
			        canvasContain.addEventListener("mouseleave", posHide);
			        canvas.addEventListener("mouseup", cfExpand);
			    }
			    else {
			        canvasContain.removeEventListener("mousemove", posDisplay);
			        canvasContain.removeEventListener("mouseleave", posHide);
			        canvas.removeEventListener("mouseup", cfExpand);
			        document.getElementById("z").innerHTML = "";
			    }
			    document.getElementById("cover0").style.display = "block";
			}

			function getGcd(x, y) {
				x = Math.abs(x); y = Math.abs(y);
				while(x != 0){
					var r = y-Math.floor(y/x)*x;
					y = x; x = r;				
				}
				return y;
			}

         function getNormGcd(x1, y1, x2, y2) {
			    if (x1 == 0 && y1 == 0) { return (x2 * x2 + d * y2 * y2) / (two * two); }
			    if (x2 == 0 && y2 == 0) { return (x1 * x1 + d * y1 * y1) / (two * two); }
			    x1 = (x1 + y1 * (1 - two)) / two; x2 = (x2 + y2 * (1 - two)) / two;
			    var gcd1 = getGcd(x1, y1), gcd2 = getGcd(x2, y2)
			    var gcd = getGcd(gcd1, gcd2);
			    x1 /= gcd; y1 /= gcd; x2 /= gcd; y2 /= gcd; gcd1 /= gcd; gcd2 /= gcd; gcd *= gcd;
			    x1 = two * x1 + (two - 1) * y1;
			    var norm1 = (x1 * x1 + d * y1 * y1) / (two * two);
			    var gcdNorm1 = getGcd(gcd2, norm1);
			    x2 /= gcdNorm1; y2 /= gcdNorm1; gcd2 /= gcdNorm1; gcd *= gcdNorm1; norm1 /= gcdNorm1;
			    x2 = two * x2 + (two - 1) * y2;
			    var norm2 = (x2 * x2 + d * y2 * y2) / (two * two);
			    var gcdNorm2 = getGcd(gcd1, norm2);
			    x1 /= gcdNorm2; y1 /= gcdNorm2; gcd1 /= gcdNorm2; gcd *= gcdNorm2; norm2 /= gcdNorm2;
			    var R = (x1 * x2 + d * y1 * y2) / two;
			    var I = (x2 * y1 - x1 * y2) / two;
			    R = (R + (1 - two) * I) / two;
			    gcd *= getGcd(norm1, getGcd(getGcd(R, I) / (gcd1 * gcd2), norm2));
			    return gcd;
			}

			function coverInflateD(i) {

			    var zList = [[0.75, 1.25, 0], [1.09066, 1.78132, 1], [-1.0285, 0.559931, 2], [-2.24062, -0.673311, 3], [1.62265, -0.337923, 4], [-0.0906598, -1.78132, 5], [-0.470661, 1.31699, 6], [-1.47066, 1.31699, 7], [1.24062, 0.673311, 8], [2.24062, 0.673311, -3], [-1.62265, 0.337923, -4], [0.249996, 2.90833, 9], [0.470661, -1.31699, -6], [1.47066, -1.31699, -7], [-1.24062, -0.673311, -8], [-0.249996, -2.90833, -9], [-1.09073, -1.78137, -1], [1.02852, -0.559913, -2], [0.0907272, 1.78137, -5]];
			    var aList = [];
			    var rectWidth = 166.789;
			    var rectLeft = originX - rectWidth / 2;
			    var rectTop = originY - scale * (Math.sqrt(31) + 0.8802195) - rectWidth / 2;
			    var color0 = "rgba(4,38,230,0.4)";
			    var color1 = "rgba(232,0,23,0.4)";
			    var thick = String(0.003 * canvasWidth * (0.1 + 3 * styles[2][0][6]));
			    for (var j = 1000; j < cfElements.length; j++) {
			        var element = cfElements[j], jj = reps[element % h][0][1];
			        if ((detList[i][1] + tor[element]) % (2 * d / two) == 0 || (jj == 0 && (detList[i][1] - tor[element]) % (2 * d / two) == 0)) {
			            color = "rgba(" + styles[3][element][8].toString() + "," + styles[3][element][9].toString() + "," + styles[3][element][10].toString() + "," + styles[3][element][6].toString() + ")";
			            break;
			        }
			    }
			    if (color0 == "") {
			        var element = cfElements[0];
			        color0 = "rgba(" + styles[3][element][8].toString() + "," + styles[3][element][9].toString() + "," + styles[3][element][10].toString() + "," + styles[3][element][6].toString() + ")";
			    }
			    var minY = Math.ceil(two * (originY - canvasWidth * (renderWidth + 1) / 2 - canvasTop) / (sqrt * scale) - 0.1);
			    var maxY = Math.floor(two * (originY + canvasWidth * (renderWidth - 1) / 2 - canvasTop) / (sqrt * scale) + 0.1);
			    var minX = Math.ceil(two * (canvasLeft - canvasWidth * (renderWidth - 1) / 2 - originX) / scale - 0.1);
			    var maxX = Math.floor(two * (canvasLeft + canvasWidth * (renderWidth + 1) / 2 - originX) / scale + 0.1);
			    while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }
			    var prime = detList[i][0];
			    for (var k = 0; k < 1; k++) {
			        for (var y = minY; y <= maxY; y++) {
			            for (var x = minX + ((minX + y) % two) ; x <= maxX; x += two) {
			                if ((x + y) % 4 != 0) {
			                    var gcdMax = 0;
			                    for (var j = 0; j < detList.length; j++) {
			                        if (detList[j][0] == prime) {
			                            var gcd = getNormGcd(x, y, detList[j][1], detList[j][2]);
			                            if (gcd % prime == 0) { gcd /= Math.abs(prime); }
			                            if (gcd > gcdMax) { gcdMax = gcd; }
			                        }
			                    }
			                    if (gcdMax >= 0) {
			                        if (k == 0) {
			                            var circle = document.createElementNS(NS, "circle");
			                            circle.setAttribute("cx", String(originX + scale * x / two));
			                            circle.setAttribute("cy", String(originY - scale * sqrt * y / two));
			                            circle.setAttribute("r", String(scale * Math.sqrt(gcdMax)));
			                            circle.setAttribute("fill", color1);
			                            circle.setAttribute("stroke", "none");
			                            arrangement.appendChild(circle);
			                        }
			                        if (k == 1 && gcdMax == 5) {
			                            var circle = document.createElementNS(NS, "circle");
			                            circle.setAttribute("cx", String(originX + scale * x / two));
			                            circle.setAttribute("cy", String(originY - scale * sqrt * y / two));
			                            circle.setAttribute("r", String(1.01845104 * scale * Math.sqrt(gcdMax)));
			                            circle.setAttribute("stroke-width", thick.toString());
			                            circle.setAttribute("fill", "none"); circle.setAttribute("stroke", "rgb(0,0,0)");
			                            arrangement.appendChild(circle);
			                        }
			                    }
			                }
			            }
			        }
			    }
			    for (var y = minY; y <= maxY; y++) {
			        for (var x = minX + ((minX + y) % two) ; x <= maxX; x += two) {
			            if ((x + y) % 4 == 0) {
			                var gcdMax = 0;
			                for (var j = 0; j < detList.length; j++) {
			                    if (detList[j][0] == prime) {
			                        var gcd = getNormGcd(x, y, detList[j][1], detList[j][2]);
			                        if (gcd % prime == 0) { gcd /= Math.abs(prime); }
			                        if (gcd > gcdMax) { gcdMax = gcd; }
			                    }
			                }
			                if (gcdMax >= 0) {
			                    var circle = document.createElementNS(NS, "circle");
			                    circle.setAttribute("cx", String(originX + scale * x / two));
			                    circle.setAttribute("cy", String(originY - scale * sqrt * y / two));
			                    circle.setAttribute("r", String(scale * Math.sqrt(gcdMax)));
			                    circle.setAttribute("fill", color0);
			                    circle.setAttribute("stroke", "none");
			                    arrangement.appendChild(circle);
			                }
			            }
			        }
			    }
			    if (1 == 0) {
			        var rect = document.createElementNS(NS, "rect");
			        rect.setAttribute("x", rectLeft);
			        rect.setAttribute("y", rectTop);
			        rect.setAttribute("width", rectWidth);
			        rect.setAttribute("height", rectWidth);
			        rect.setAttribute("fill", "none");
			        rect.setAttribute("stroke-width", thick.toString());
			        rect.setAttribute("stroke", "rgb(0,0,0)");
			        arrangement.appendChild(rect);
			    }
			    if (1 == 1) {
			        if (!document.getElementById("labels0")) {
			            for (var k = 0; k < zList.length; k++) {
			                var label = document.createElementNS(NS, "g");
			                var rect = document.createElementNS(NS, "rect");
			                rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			                rect.setAttribute("x", String(-0.011 * initWidth));
			                rect.setAttribute("y", String(-0.011 * initWidth));
			                rect.setAttribute("width", String(0.022 * initWidth));
			                rect.setAttribute("height", String(0.022 * initWidth));
			                rect.setAttribute("rx", String(0.004 * initWidth));
			                rect.setAttribute("ry", String(0.004 * initWidth));
			                rect.setAttribute("stroke", "rgb(0,0,0)"); rect.setAttribute("fill", "rgb(255,255,255)");
			                rect.setAttribute("stroke-width", String(0.0004 * initWidth));
			                label.appendChild(rect);
			                var text = document.createElementNS(NS, "text");
			                text.setAttribute("font-size", String(0.02 * initWidth));
			                text.setAttribute("fill", "rgb(0,0,0)");
			                text.setAttribute("x", "0"); text.setAttribute("y", String(0.007 * initWidth));
			                text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			                text.style.pointerEvents = "none"; text.innerHTML = zList[k][2].toString();
			                label.appendChild(text); selectLabels.appendChild(label);
			                label.setAttribute("transform", "translate(" + String(originX + scale * zList[k][0]) + "," + String(originY - scale * zList[k][1]) + ") scale(" + String(canvasWidth / initWidth) + ")");

			            }
			            for (var k = 0; k < aList.length; k++) {
			                var circle = document.createElementNS(NS, "circle");
			                circle.setAttribute("cx", String(originX + scale * aList[k][0] / two));
			                circle.setAttribute("cy", String(originY - scale * sqrt * aList[k][1] / two));
			                circle.setAttribute("r", String(scale * Math.sqrt(aList[k][2])));
			                circle.setAttribute("fill", "none"); circle.setAttribute("stroke", "rgb(0,0,0)");
			                selectCircles.appendChild(circle); ++selectCount;
			                var circle = document.createElementNS(NS, "circle");
			                circle.setAttribute("cx", String(originX + scale * aList[k][0] / two));
			                circle.setAttribute("cy", String(originY - scale * sqrt * aList[k][1] / two));
			                circle.setAttribute("r", String(canvasWidth * 0.005));
			                circle.setAttribute("fill", "rgb(0,0,0)"); circle.setAttribute("stroke", "none");
			                selectCircles.appendChild(circle); ++selectCount;
			            }
			        }
			    }
			}

			function cfExpand() {

			    while (convergeTable.lastChild) { convergeTable.removeChild(convergeTable.lastChild); }
			    while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			    while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			    selectLabelCount = 0;
			    var i = 0; infoArray = [];
			    while (infoCount > 0) {
			        var element = canvas.childNodes[i];
			        if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			        else { i++; }
			    }
			    canvas.removeEventListener("mouseup", cfExpand);
			    canvasContain.removeEventListener("mousemove", posDisplay);
			    canvasContain.removeEventListener("mouseleave", posHide);
			    var admissibleGCDs = []
			    for (var i = 1; i <= currentPrin; i++) {
			        if (currentPrin % i == 0) {
			            if (document.getElementById("checkBox8," + i.toString()).innerHTML != "") {
			                admissibleGCDs.push(i);
			            }
			        }
			    }
			    var epsilon = parseFloat(epsilonCell.innerHTML);
			    if (1 == 1) { zX = 264; zY = 56; zD = 228; }
			    var count = 0; startzX = zX; startzY = zY; startzD = zD;
			    var tempZX = (zX * detList[0][1] - d * zY * detList[0][2]) / two;
			    zY = (zY * detList[0][1] + zX * detList[0][2]) / two; zX = tempZX;
			    var gcd = getGcd((zX + (1 - two) * zY) / two, getGcd(zY, zD));
			    zX /= gcd; zY /= gcd; zD /= gcd;
			    var gcdABCD = 1; detChoice = 0;
			    var matrix = [[two, 0], [0, 0], [0, 0], [detList[0][1], detList[0][2]]];
			    var detNorm = currentPrin;
			    var oCirc = document.createElementNS(NS, "circle");
			    oCirc.setAttribute("fill", "rgb(0,0,0)");
			    oCirc.setAttribute("stroke", "none");
			    oCirc.setAttribute("r", String(canvasWidth * 0.0075));
			    oCirc.setAttribute("cx", originX.toString());
			    oCirc.setAttribute("cy", originY.toString());
			    infoCircles.appendChild(oCirc);
			    if (coverings == 1) {

			        var zPoint = document.createElementNS(NS, "g");
			        var zCirc = document.createElementNS(NS, "circle");
			        zCirc.setAttribute("r", String(canvasWidth * 0.015));
			        zCirc.setAttribute("cx", "0");
			        zCirc.setAttribute("cy", "0");
			        zCirc.setAttribute("fill", "rgb(255,255,255)");
			        zCirc.setAttribute("stroke", "rgb(0,0,0)");
			        zCirc.setAttribute("stroke-width", String(canvasWidth * 0.0016));
                    zPoint.appendChild(zCirc);
			        var zText = document.createElementNS(NS, "text");
			        zText.setAttribute("font-size", String(0.03 * canvasWidth));
			        zText.setAttribute("fill", "rgb(0,0,0)");
			        zText.setAttribute("x", "0"); zText.setAttribute("y", String(0.01 * canvasWidth));
			        zText.setAttribute("text-anchor", "middle"); zText.setAttribute("font-weight", "bold");
			        zText.style.pointerEvents = "none";
			        zPoint.appendChild(zText);
			        selectLabels.appendChild(zPoint);
			        ++selectLabelCount;

			        var aCirc = document.createElementNS(NS, "circle");
			        aCirc.setAttribute("fill", "none");
			        aCirc.setAttribute("stroke", "rgb(0,0,0)");
			        aCirc.setAttribute("stroke-width", String(canvasWidth * 0.00192));
			        infoCircles.appendChild(aCirc);
			        expand();
			    }
			    else {
			        var found = [], initCentX = originX + scale * startzX / (two * startzD), initCentY = originY - scale * sqrt * startzY / (two * startzD);
			        var label = document.createElementNS(NS, "g");
			        label.setAttribute("transform", "translate(" + initCentX.toString() + "," + initCentY.toString() + ") scale(" + String(canvasWidth / initWidth) + ")");
			        var rect = document.createElementNS(NS, "rect");
			        rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			        rect.setAttribute("x", String(-0.011 * initWidth));
			        rect.setAttribute("y", String(-0.011 * initWidth));
			        rect.setAttribute("width", String(0.022 * initWidth));
			        rect.setAttribute("height", String(0.022 * initWidth));
			        rect.setAttribute("rx", String(0.004 * initWidth));
			        rect.setAttribute("ry", String(0.004 * initWidth));
			        rect.setAttribute("stroke", "rgb(0,0,0)");
			        rect.setAttribute("stroke-width", String(0.0012 * initWidth));
			        rect.setAttribute("fill", "rgb(255,255,255)");
			        label.appendChild(rect);
			        var text = document.createElementNS(NS, "text");
			        text.setAttribute("font-size", String(0.02 * initWidth));
			        text.setAttribute("fill", "rgb(0,0,0)");
			        text.setAttribute("x", "0"); text.setAttribute("y", String(0.007 * initWidth));
			        text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			        text.style.pointerEvents = "none"; text.innerHTML = "&#x1d467;";
			        label.appendChild(text); selectLabels.appendChild(label);
			        var newCanvasWidth = 0.7 * initWidth;
			        var hypot = Math.abs(newCanvasWidth - canvasWidth) / 1.5;
			        if (hypot > 0.001) {
			            var intervalW = 2 * (newCanvasWidth - canvasWidth) / (Math.floor(1 / delta) * hypot);
			            var intervalL = 2 * (initCentX - newCanvasWidth / 2 - canvasLeft) / (Math.floor(1 / delta) * hypot);
			            var intervalT = 2 * (initCentY - newCanvasWidth / 2 - canvasTop) / (Math.floor(1 / delta) * hypot);
			            var boundW = Math.max(0.002, Math.abs(2 * intervalW));
			        }
			        else { var intervalW = 0; var boundW = 0.005; }
			        var move3 = setInterval(function () {

			            canvasWidth += intervalW; canvasLeft += intervalL; canvasTop += intervalT;
			            canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			            if (Math.abs(canvasWidth - newCanvasWidth) < boundW) {

			                clearInterval(move3);
			                canvasWidth = newCanvasWidth; canvasLeft = initCentX - canvasWidth / 2; canvasTop = initCentY - canvasWidth / 2; delta = canvasWidth / containWidth;
			                canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			                for (var j = 0; j < selectLabelCount; j++) {
			                    var label = document.getElementById("labels" + j.toString()).parentNode;
			                    if (label) {
			                        var transform = label.getAttribute("transform"); transform = transform.split(" ");
			                        label.setAttribute("transform", transform[0] + " scale(" + String(canvasWidth / initWidth) + ")");
			                    }
			                }
			                for (var i = 0; i < cfElements.length; i++) { render(cfElements[i]); }
			                setTimeout(function () { expand(); }, 200);
			            }
			        }, 50);
			    }

			    function expand() {

			        //setup
			        var centX = zX / (two * zD), centY = sqrt * zY / (two * zD);
			        var canvasX = canvasY = 0;
			        if (count == 0) {
			            canvasX = (centX * detList[0][1] + sqrt * centY * detList[0][2]) / (currentPrin * two);
			            canvasY = (centY * detList[0][1] - sqrt * centX * detList[0][2]) / (currentPrin * two);
			            if (coverings == 1) {
			                zPoint.setAttribute("transform", "translate(" + String(originX + scale * canvasX) + "," + String(originY - scale * canvasY) + ")");
			            }
			        }


			        //get smallest shift for reduction
			        var N = 0, check = 0;
			        while (check == 0) {
			            var maxY = Math.floor(Math.sqrt(two * two * N / d) + 0.01);
			            loop: for (var y = -1 * maxY; y <= maxY; y++) {
			                var x = Math.floor(Math.sqrt(two * two * N - d * y * y) + 0.5);
			                if (x * x + d * y * y == two * two * N) {
			                    var pX = (matrix[0][0] * x - d * matrix[0][1] * y) / two + matrix[2][0];
			                    var pY = (matrix[0][0] * y + matrix[0][1] * x) / two + matrix[2][1];
			                    var qX = (matrix[1][0] * x - d * matrix[1][1] * y) / two + matrix[3][0];
			                    var qY = (matrix[1][0] * y + matrix[1][1] * x) / two + matrix[3][1];
			                    var redPX = pX - two * gcdABCD * currentPrin * Math.floor(pX / (two * gcdABCD * currentPrin) + 0.5);
			                    var redPY = pY - two * gcdABCD * currentPrin * Math.floor(pY / (two * gcdABCD * currentPrin) + 0.5);
			                    var redQX = qX - two * gcdABCD * currentPrin * Math.floor(qX / (two * gcdABCD * currentPrin) + 0.5);
			                    var redQY = qY - two * gcdABCD * currentPrin * Math.floor(qY / (two * gcdABCD * currentPrin) + 0.5);
			                    if (getNormGcd(redPX, redPY, redQX, redQY) % (gcdABCD * currentPrin) == 0) {
			                        var redShiftX = x; var redShiftY = y; check = 1; break loop;
			                    }
			                }
			            }
			            N++;
			        }


			        //reduce matrix
			        matrix[2][0] += (matrix[0][0] * redShiftX - d * matrix[0][1] * redShiftY) / two;
			        matrix[2][1] += (matrix[0][0] * redShiftY + matrix[0][1] * redShiftX) / two;
			        matrix[3][0] += (matrix[1][0] * redShiftX - d * matrix[1][1] * redShiftY) / two;
			        matrix[3][1] += (matrix[1][0] * redShiftY + matrix[1][1] * redShiftX) / two;


			        //get determinant index
			        var index = 0, tempMatrix = [];
			        for (var i = 0; i < 4; i++) {
			            var redX = matrix[i][0] - two * gcdABCD * currentPrin * Math.floor(matrix[i][0] / (two * gcdABCD * currentPrin) + 0.5);
			            var redY = matrix[i][1] - two * gcdABCD * currentPrin * Math.floor(matrix[i][1] / (two * gcdABCD * currentPrin) + 0.5);
			            tempMatrix.push([redX, redY]);
			        }
			        for (var i = 0; i < detList.length; i++) {
			            var check = 0;
			            for (var j = 0; j < 4; j++) {
			                var m = parseInt(j / 2), n = 2 + (j % 2);
			                var x = (tempMatrix[m][0] * tempMatrix[n][0] + d * tempMatrix[m][1] * tempMatrix[n][1]) / (gcdABCD * two);
			                var y = (tempMatrix[m][1] * tempMatrix[n][0] - tempMatrix[n][1] * tempMatrix[m][0]) / (gcdABCD * two);
			                var tempX = (x * detList[i][1] - d * y * detList[i][2]) / two;
			                y = (x * detList[i][2] + y * detList[i][1]) / two; x = (tempX + y * (1 - two)) / two;
			                if (x % currentPrin != 0 || y % currentPrin != 0) { check = 1; break; }
			            }
			            if (check == 0) { index = i; break; }
			        }



			        //translate index covering and show

			        var canvasShiftX = (redShiftX * detList[0][1] + d * redShiftY * detList[0][2]) / (two * two * currentPrin);
			        var canvasShiftY = sqrt * (redShiftY * detList[0][1] - redShiftX * detList[0][2]) / (two * two * currentPrin);
			        if (coverings == 1) {
			            var cover = document.getElementById("cover" + index.toString());
			            cover.setAttribute("transform", "translate(" + String(scale * canvasShiftX) + " " + String(-1 * scale * canvasShiftY) + ")");
			            if (count == 0 && document.getElementById("cover" + detChoice.toString()).style.display == "none") {
			                document.getElementById("cover2").style.display = "none";
			                cover.style.display = "block";
			            }
			        }


			        //move z in window
			        centX -= redShiftX / two; centY -= sqrt * redShiftY / two;
			        var closeShiftX = closeShiftY = 0;
			        canvasX = (centX * detList[0][1] + sqrt * centY * detList[0][2]) / (currentPrin * two);
			        canvasY = (centY * detList[0][1] - sqrt * centX * detList[0][2]) / (currentPrin * two);
			        if (coverings == 1) {
			            var startNorm = centX * centX + centY * centY;
			            while (Math.max(Math.abs(canvasX), Math.abs(canvasY)) > canvasWidth / (2 * scale)) {
			                for (var i = 1; i < smallest9[index].length; i++) {
			                    var smallestX = (smallest9[index][i][0] * detList[0][1] + d * smallest9[index][i][1] * detList[0][2]) / (currentPrin * two * two);
			                    var smallestY = sqrt * (smallest9[index][i][1] * detList[0][1] - smallest9[index][i][0] * detList[0][2]) / (currentPrin * two * two);
			                    var dist = (canvasX - smallestX) * (canvasX - smallestX) + (canvasY - smallestY) * (canvasY - smallestY);
			                    if (dist < startNorm) {
			                        canvasX -= smallestX; canvasY -= smallestY;
			                        centX -= smallest9[index][i][0] / two; centY -= sqrt * smallest9[index][i][1] / two;
			                        closeShiftX += smallest9[index][i][0]; closeShiftY += smallest9[index][i][1];
			                        startNorm = dist; break;
			                    }
			                }
			            }
			        }
			        canvasX += canvasShiftX; canvasY += canvasShiftY;




			        //get "a" for shifted z value
			        var minDist = epsilon; aChoice = [], prime = detList[index][0], detX = detList[index][1], detY = detList[index][2];
			        for (var i = 0; i < detList.length; i++) {
			            if (detList[i][0] == prime) {
			                var iX = detList[i][1], iY = detList[i][2];
			                var tempCentX = (centX * (iX * detX + d * iY * detY) - sqrt * centY * (iY * detX - iX * detY)) / (two * two * prime * currentPrin);
			                var tempCentY = (centY * (iX * detX + d * iY * detY) + sqrt * centX * (iY * detX - iX * detY)) / (two * two * prime * currentPrin);
			                var approxY = Math.floor(tempCentY * two / sqrt + 0.5);
			                var approxX = two * Math.floor(tempCentX - (approxY % two) / two + 0.5) + approxY % two;
			                tempCentX -= approxX / two; tempCentY -= sqrt * approxY / two;
			                for (var j = 0; j < ball.length; j++) {
			                    var dist = (tempCentX - ball[j][0] / two) * (tempCentX - ball[j][0] / two) + (tempCentY - sqrt * ball[j][1] / two) * (tempCentY - sqrt * ball[j][1] / two);
			                    var gcd = getNormGcd(approxX + ball[j][0], approxY + ball[j][1], iX, iY);
			                    if (gcd % prime == 0) { gcd /= Math.abs(prime); }
			                    if (admissibleGCDs.indexOf(gcd) != -1 && Math.sqrt(dist / gcd) < minDist) {
			                        minDist = Math.sqrt(dist / gcd);
			                        aChoice = [gcd, iX, iY, approxX + ball[j][0], approxY + ball[j][1]];
			                    }
			                }
			            }
			        }

			        if (minDist < epsilon) {
			            //get new matrix
			            gcd = aChoice[0];
			            var uX = (aChoice[1] * detX + d * aChoice[2] * detY) / (two * prime);
			            var uY = (aChoice[2] * detX - aChoice[1] * detY) / (two * prime);
			            var pX = (matrix[0][0] * closeShiftX - d * matrix[0][1] * closeShiftY) / two + matrix[2][0];
			            var pY = (matrix[0][0] * closeShiftY + matrix[0][1] * closeShiftX) / two + matrix[2][1];
			            var qX = (matrix[1][0] * closeShiftX - d * matrix[1][1] * closeShiftY) / two + matrix[3][0];
			            var qY = (matrix[1][0] * closeShiftY + matrix[1][1] * closeShiftX) / two + matrix[3][1];
			            matrix[2][0] = (pX * uX - d * pY * uY) / (two * currentPrin);
			            matrix[2][1] = (pY * uX + pX * uY) / (two * currentPrin);
			            matrix[3][0] = (qX * uX - d * qY * uY) / (two * currentPrin);
			            matrix[3][1] = (qY * uX + qX * uY) / (two * currentPrin);
			            pX = (matrix[0][0] * aChoice[3] - d * matrix[0][1] * aChoice[4]) / two + matrix[2][0];
			            var pY = (matrix[0][0] * aChoice[4] + matrix[0][1] * aChoice[3]) / two + matrix[2][1];
			            var qX = (matrix[1][0] * aChoice[3] - d * matrix[1][1] * aChoice[4]) / two + matrix[3][0];
			            var qY = (matrix[1][0] * aChoice[4] + matrix[1][1] * aChoice[3]) / two + matrix[3][1];
			            matrix[2] = [gcd * matrix[0][0], gcd * matrix[0][1]];
			            matrix[3] = [gcd * matrix[1][0], gcd * matrix[1][1]];
			            matrix[0] = [pX, pY]; matrix[1] = [qX, qY];
			            gcdABCD *= gcd; detNorm *= gcd;



			            //get new z but don't reflect yet
			            tempZX = ((zX - zD * (redShiftX + closeShiftX)) * uX - d * (zY - zD * (redShiftY + closeShiftY)) * uY) / two;
			            zY = ((zX - zD * (redShiftX + closeShiftX)) * uY + (zY - zD * (redShiftY + closeShiftY)) * uX) / two; zX = tempZX;
			            zD *= currentPrin;
			            zX -= zD * aChoice[3]; zY -= zD * aChoice[4];


			            //scale matrix to reduce entries
			            for (var i = 0; i < reducers.length; i++) {
			                var redX = reducers[i][0], redY = reducers[i][1];
			                var redN = (redX * redX + d * redY * redY) / (two * two);
			                var check = 0;
			                while (check == 0) {
			                    if (detNorm % (currentPrin * redN * redN) == 0) {
			                        for (var j = 0; j < 4; j++) {
			                            var x = (matrix[j][0] * redX + d * matrix[j][1] * redY) / two;
			                            var y = (matrix[j][1] * redX - matrix[j][0] * redY) / two;
			                            x = (x + (1 - two) * y) / two;
			                            if (x % redN != 0 || y % redN != 0) { check = 1; break; }
			                        }
			                        if (check == 0) {
			                            for (var j = 0; j < 4; j++) {
			                                var x = (matrix[j][0] * redX + d * matrix[j][1] * redY) / two;
			                                var y = (matrix[j][1] * redX - matrix[j][0] * redY) / two;
			                                matrix[j][0] = x / redN; matrix[j][1] = y / redN;
			                            }
			                            gcdABCD /= redN; detNorm /= (redN * redN);
			                        }
			                    }
			                    else { check = 1; }
			                }
			            }

			            //display info
			            var aCentX = (uX * aChoice[3] + d * uY * aChoice[4]) / two;
			            var aCentY = (uX * aChoice[4] - uY * aChoice[3]) / two;
			            var row = document.createElement("tr");
			            var cell = document.createElement("td");
			            cell.className = "infoCell";
			            if (currentPrin != 1) { cell.innerHTML = currentPrin.toString(); }
			            var string = "a", aX = aCentX + currentPrin * (closeShiftX + redShiftX), aY = aCentY + currentPrin * (closeShiftY + redShiftY);
			            cell.innerHTML += string.italics() + "<sub class='subScript'>" + count.toString() + "</sub>&nbsp;=&nbsp;";
			            cell.innerHTML += getEntry((aX + (1 - two) * aY) / two, aY);
			            row.appendChild(cell);
			            var cell = document.createElement("td");
			            cell.className = "infoCell";
			            cell.innerHTML = "&#124;&#124;&#x1D51F;<sub class='subScript'>" + count.toString() + "</sub>&#124;&#124;&nbsp;=&nbsp;" + gcd.toString();
			            row.appendChild(cell);
			            cell = document.createElement("td");
			            cell.className = "infoCell";
			            if (currentPrin != 1) { cell.innerHTML = currentPrin.toString(); }
			            string = "u";
			            cell.innerHTML += string.italics() + "<sub class='subScript'>" + count.toString() + "</sub>&nbsp;=&nbsp;";
			            cell.innerHTML += getEntry((uX + (1 - two) * uY) / two, uY);
			            row.appendChild(cell);
			            cell = document.createElement("td");
			            cell.className = "infoCell";
			            string = "p";
			            cell.innerHTML += string.italics() + "<sub class='subScript'>" + count.toString() + "</sub>&nbsp;=&nbsp;";
			            cell.innerHTML += getEntry((matrix[0][0] + (1 - two) * matrix[0][1]) / two, matrix[0][1]);
			            row.appendChild(cell);
			            cell = document.createElement("td");
			            cell.className = "infoCell";
			            string = "q";
			            cell.innerHTML += string.italics() + "<sub class='subScript'>" + count.toString() + "</sub>&nbsp;=&nbsp;";
			            cell.innerHTML += getEntry((matrix[1][0] + (1 - two) * matrix[1][1]) / two, matrix[1][1]);
			            row.appendChild(cell);
			            convergeTable.appendChild(row);

			            if (coverings == 1) {
			                //get "a" circle center
			                aCentX /= (two * currentPrin);
			                aCentY *= sqrt / (two * currentPrin);
			                aCentX += redShiftX / two; aCentY += sqrt * redShiftY / two;
			                var aCanvasX = (aCentX * detList[0][1] + sqrt * aCentY * detList[0][2]) / (two * currentPrin);
			                var aCanvasY = (aCentY * detList[0][1] - sqrt * aCentX * detList[0][2]) / (two * currentPrin);
			                if (count % 2 != 0) { aCanvasY *= -1; }
			                aCanvasX = originX + scale * aCanvasX; aCanvasY = originY - scale * aCanvasY;
			            }
			        }

			        if (coverings == 1) {
			            //animate svg and get new zPoint

			            var oldCanvas = zPoint.getAttribute("transform");
			            oldCanvas = oldCanvas.substring(oldCanvas.indexOf("(") + 1);
			            oldCanvas = oldCanvas.slice(0, -1); oldCanvas = oldCanvas.split(",");
			            var oldCanvasX = parseFloat(oldCanvas[0]);
			            var oldCanvasY = parseFloat(oldCanvas[1]);
			            var newCanvasX = originX + scale * canvasX;
			            var newCanvasY = originY - scale * canvasY;
			            if (count % 2 != 0) { newCanvasY = originY + scale * canvasY; }
			            var intervalXX = intervalYY = boundXX = boundYY = 0;
			            var hypot = Math.sqrt((oldCanvasX - newCanvasX) * (oldCanvasX - newCanvasX) + (oldCanvasY - newCanvasY) * (oldCanvasY - newCanvasY)) / 1.5;
			            if (hypot > 0.001) {
			                intervalXX = 1 * (newCanvasX - oldCanvasX) / (Math.floor(1 / delta) * hypot);
			                intervalYY = 1 * (newCanvasY - oldCanvasY) / (Math.floor(1 / delta) * hypot);
			                boundXX = Math.max(0.001, Math.abs(2 * intervalXX)); boundYY = Math.max(0.001, Math.abs(2 * intervalYY));
			            }
			            else { intervalXX = 0; intervalYY = 0; boundXX = 0.005; boundYY = 0.005; }

			            var move1 = setInterval(function () {
			                oldCanvasX += intervalXX; oldCanvasY += intervalYY;
			                zPoint.setAttribute("transform", "translate(" + oldCanvasX.toString() + "," + oldCanvasY.toString() + ")");

			                if (Math.abs(newCanvasX - oldCanvasX) < boundXX && Math.abs(newCanvasY - oldCanvasY) < boundYY) {

			                    clearInterval(move1);
			                    zPoint.setAttribute("transform", "translate(" + newCanvasX.toString() + "," + newCanvasY.toString() + ")");
			                    zText.innerHTML = count.toString();

			                    if (minDist == epsilon) {

			                        canvas.addEventListener("mouseup", cfExpand);
			                        canvasContain.addEventListener("mousemove", posDisplay);
			                        canvasContain.addEventListener("mouseleave", posHide);
			                        return;
			                    }

			                    var stall = 0;

			                    var move2 = setInterval(function () {

			                        stall++;

			                        if (stall == 40 || (count > 0 && stall == 20)) {

			                            clearInterval(move2);

			                            if (index != detChoice) {
			                                document.getElementById("cover" + detChoice.toString()).style.display = "none";
			                                cover.style.display = "block"; detChoice = index;
			                            }

			                            stall = 0;

			                            var move4 = setInterval(function () {

			                                stall++;

			                                if (stall == 60 || count != 2) {

			                                    clearInterval(move4);

			                                    oldCanvasX = newCanvasX; oldCanvasY = newCanvasY;
			                                    newCanvasX += originX - aCanvasX; newCanvasY += originY - aCanvasY;
			                                    var rad = scale * epsilon * Math.sqrt(gcd / currentPrin);
			                                    aCirc.setAttribute("cx", aCanvasX.toString());
			                                    aCirc.setAttribute("cy", aCanvasY.toString());
			                                    aCirc.setAttribute("r", rad.toString());


			                                    //make labels
			                                    tempX = scale * (closeShiftX * detList[0][1] + d * closeShiftY * detList[0][2]) / (two * two * currentPrin);
			                                    closeShiftY = scale * sqrt * (closeShiftY * detList[0][1] - closeShiftX * detList[0][2]) / (two * two * currentPrin); closeShiftX = tempX;
			                                    var label = document.createElementNS(NS, "g");
			                                    label.setAttribute("transform", "translate(" + String(aCanvasX + closeShiftX) + "," + String(aCanvasY - closeShiftY) + ") scale(" + String(canvasWidth / initWidth) + ")");
			                                    var rect = document.createElementNS(NS, "rect");
			                                    rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			                                    rect.setAttribute("x", String(-0.0135 * initWidth));
			                                    rect.setAttribute("y", String(-0.0135 * initWidth));
			                                    rect.setAttribute("width", String(0.027 * initWidth));
			                                    rect.setAttribute("height", String(0.027 * initWidth));
			                                    rect.setAttribute("rx", String(0.004 * initWidth));
			                                    rect.setAttribute("ry", String(0.004 * initWidth));
			                                    rect.setAttribute("stroke", "rgb(0,0,0)");
			                                    rect.setAttribute("stroke-width", String(0.0016 * initWidth));
			                                    rect.setAttribute("fill", "rgb(255,255,255)");
			                                    label.appendChild(rect);
			                                    var text = document.createElementNS(NS, "text");
			                                    text.setAttribute("font-size", String(0.03 * initWidth));
			                                    text.setAttribute("fill", "rgb(0,0,0)");
			                                    text.setAttribute("x", "0"); text.setAttribute("y", String(0.01 * initWidth));
			                                    text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			                                    text.style.pointerEvents = "none"; text.innerHTML = count.toString();
			                                    label.appendChild(text); selectLabels.appendChild(label);

			                                    var hypot = Math.sqrt((originX - aCanvasX) * (originX - aCanvasX) + (originY - aCanvasY) * (originY - aCanvasY)) / 1.5;
			                                    if (hypot > 0.001) {
			                                        var intervalX = 1 * (originX - aCanvasX) / (Math.floor(1 / delta) * hypot);
			                                        var intervalY = 1 * (originY - aCanvasY) / (Math.floor(1 / delta) * hypot);
			                                        var boundX = Math.max(0.001, Math.abs(2 * intervalX)), boundY = Math.max(0.001, Math.abs(2 * intervalY));
			                                    }
			                                    else { var intervalX = intervalY = 0; var boundX = boundY = 0.005; }

			                                    var move3 = setInterval(function () {

			                                        aCanvasX += intervalX; aCanvasY += intervalY;
			                                        oldCanvasX += intervalX; oldCanvasY += intervalY;
			                                        aCirc.setAttribute("cx", aCanvasX.toString());
			                                        aCirc.setAttribute("cy", aCanvasY.toString());
			                                        zPoint.setAttribute("transform", "translate(" + oldCanvasX.toString() + "," + oldCanvasY.toString() + ")");

			                                        if (Math.abs(aCanvasX - originX) < boundX && Math.abs(aCanvasY - originY) < boundY) {

			                                            clearInterval(move3);
			                                            aCirc.setAttribute("cx", originX.toString());
			                                            aCirc.setAttribute("cy", originY.toString());
			                                            zPoint.setAttribute("transform", "translate(" + newCanvasX.toString() + "," + newCanvasY.toString() + ")");
			                                            var normZ = (zX * zX + d * zY * zY) / (two * two);
			                                            if (normZ != 0) {
			                                                zX *= gcd * zD; zY *= -1 * gcd * zD; zD = normZ;
			                                                gcd = getGcd((zX + (1 - two) * zY) / two, getGcd(zY, zD));
			                                                zX /= gcd; zY /= gcd; zD /= gcd; count++;
			                                                expand();
			                                            }
			                                            else {
			                                                //get smallest shift for reduction
			                                                var N = 0, check = 0;
			                                                while (check == 0) {
			                                                    var maxY = Math.floor(Math.sqrt(two * two * N / d) + 0.01);
			                                                    loop: for (var y = -1 * maxY; y <= maxY; y++) {
			                                                        var x = Math.floor(Math.sqrt(two * two * N - d * y * y) + 0.5);
			                                                        if (x * x + d * y * y == two * two * N) {
			                                                            var pX = (matrix[0][0] * x - d * matrix[0][1] * y) / two + matrix[2][0];
			                                                            var pY = (matrix[0][0] * y + matrix[0][1] * x) / two + matrix[2][1];
			                                                            var qX = (matrix[1][0] * x - d * matrix[1][1] * y) / two + matrix[3][0];
			                                                            var qY = (matrix[1][0] * y + matrix[1][1] * x) / two + matrix[3][1];
			                                                            var redPX = pX - two * gcdABCD * currentPrin * Math.floor(pX / (two * gcdABCD * currentPrin) + 0.5);
			                                                            var redPY = pY - two * gcdABCD * currentPrin * Math.floor(pY / (two * gcdABCD * currentPrin) + 0.5);
			                                                            var redQX = qX - two * gcdABCD * currentPrin * Math.floor(qX / (two * gcdABCD * currentPrin) + 0.5);
			                                                            var redQY = qY - two * gcdABCD * currentPrin * Math.floor(qY / (two * gcdABCD * currentPrin) + 0.5);
			                                                            if (getNormGcd(redPX, redPY, redQX, redQY) % (gcdABCD * currentPrin) == 0) {
			                                                                var redShiftX = x; var redShiftY = y; check = 1; break loop;
			                                                            }
			                                                        }
			                                                    }
			                                                    N++;
			                                                }


			                                                //reduce matrix
			                                                matrix[2][0] += (matrix[0][0] * redShiftX - d * matrix[0][1] * redShiftY) / two;
			                                                matrix[2][1] += (matrix[0][0] * redShiftY + matrix[0][1] * redShiftX) / two;
			                                                matrix[3][0] += (matrix[1][0] * redShiftX - d * matrix[1][1] * redShiftY) / two;
			                                                matrix[3][1] += (matrix[1][0] * redShiftY + matrix[1][1] * redShiftX) / two;



			                                                //get determinant index
			                                                index = 0; tempMatrix = [];
			                                                for (var i = 0; i < 4; i++) {
			                                                    var redX = matrix[i][0] - two * gcdABCD * currentPrin * Math.floor(matrix[i][0] / (two * gcdABCD * currentPrin) + 0.5);
			                                                    var redY = matrix[i][1] - two * gcdABCD * currentPrin * Math.floor(matrix[i][1] / (two * gcdABCD * currentPrin) + 0.5);
			                                                    tempMatrix.push([redX, redY]);
			                                                }
			                                                for (var i = 0; i < detList.length; i++) {
			                                                    var check = 0;
			                                                    for (var j = 0; j < 4; j++) {
			                                                        var m = parseInt(j / 2), n = 2 + (j % 2);
			                                                        var x = (tempMatrix[m][0] * tempMatrix[n][0] + d * tempMatrix[m][1] * tempMatrix[n][1]) / (gcdABCD * two);
			                                                        var y = (tempMatrix[m][1] * tempMatrix[n][0] - tempMatrix[n][1] * tempMatrix[m][0]) / (gcdABCD * two);
			                                                        var tempX = (x * detList[i][1] - d * y * detList[i][2]) / two;
			                                                        y = (x * detList[i][2] + y * detList[i][1]) / two; x = (tempX + y * (1 - two)) / two;
			                                                        if (x % currentPrin != 0 || y % currentPrin != 0) { check = 1; break; }
			                                                    }
			                                                    if (check == 0) { tempIndex = i; break; }
			                                                }



			                                                //translate index covering and show
			                                                var canvasShiftX = (redShiftX * detList[0][1] + d * redShiftY * detList[0][2]) / (two * two * currentPrin);
			                                                var canvasShiftY = sqrt * (redShiftY * detList[0][1] - redShiftX * detList[0][2]) / (two * two * currentPrin);
			                                                var cover = document.getElementById("cover" + index.toString());
			                                                cover.setAttribute("transform", "translate(" + String(-1 * scale * canvasShiftX) + " " + String(scale * canvasShiftY) + ")");
			                                                if (index != detChoice && 1 == 0) {
			                                                    document.getElementById("cover" + detChoice.toString()).style.display = "none";
			                                                    cover.style.display = "block"; detChoice = index;
			                                                }

			                                                canvas.addEventListener("mouseup", cfExpand);
			                                                canvasContain.addEventListener("mousemove", posDisplay);
			                                                canvasContain.addEventListener("mouseleave", posHide);
			                                            }
			                                        }
			                                    }, 17);
			                                }
			                            }, 50);
			                        }
			                    }, 50);
			                }
			            }, 17);
			        }

			        else {
			            count++;
			            if (minDist == epsilon) {
			                canvas.addEventListener("mouseup", cfExpand);
			                canvasContain.addEventListener("mousemove", posDisplay);
			                canvasContain.addEventListener("mouseleave", posHide);
			                return;
			            }

			            var normQ = matrix[1][0] * matrix[1][0] + d * matrix[1][1] * matrix[1][1];
			            if (normQ != 0) {
			                var approxCentX = originX + scale * (matrix[0][0] * matrix[1][0] + d * matrix[0][1] * matrix[1][1]) / normQ;
			                var approxCentY = originY - scale * sqrt * (matrix[0][1] * matrix[1][0] - matrix[0][0] * matrix[1][1]) / normQ;
			                var label = document.createElementNS(NS, "g");
			                label.setAttribute("transform", "translate(" + approxCentX.toString() + "," + approxCentY.toString() + ") scale(" + String(canvasWidth / initWidth) + ")");
			                var rect = document.createElementNS(NS, "rect");
			                rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			                rect.setAttribute("x", String(-0.011 * initWidth));
			                rect.setAttribute("y", String(-0.011 * initWidth));
			                rect.setAttribute("width", String(0.022 * initWidth));
			                rect.setAttribute("height", String(0.022 * initWidth));
			                rect.setAttribute("rx", String(0.004 * initWidth));
			                rect.setAttribute("ry", String(0.004 * initWidth));
			                rect.setAttribute("stroke", "rgb(0,0,0)");
			                rect.setAttribute("stroke-width", String(0.0012 * initWidth));
			                rect.setAttribute("fill", "rgb(255,255,255)");
			                label.appendChild(rect);
			                var text = document.createElementNS(NS, "text");
			                text.setAttribute("font-size", String(0.02 * initWidth));
			                text.setAttribute("fill", "rgb(0,0,0)");
			                text.setAttribute("x", "0"); text.setAttribute("y", String(0.007 * initWidth));
			                text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			                text.style.pointerEvents = "none"; text.innerHTML = count.toString();
			                label.appendChild(text); selectLabels.insertBefore(label, selectLabels.lastChild);
			            }

			            var r = (matrix[1][0] * matrix[3][1] - matrix[1][1] * matrix[3][0]) / (gcdABCD * two);
			            var q = (matrix[0][0] * matrix[2][1] - matrix[0][1] * matrix[2][0]) / (gcdABCD * two);
			            var Re = two * (matrix[0][0] * matrix[3][0] - matrix[1][0] * matrix[2][0] + (matrix[0][1] * matrix[3][1] - matrix[1][1] * matrix[2][1]) * d) / (gcdABCD * two * two);
			            var Im = (matrix[0][1] * matrix[3][0] - matrix[0][0] * matrix[3][1] - matrix[1][0] * matrix[2][1] + matrix[1][1] * matrix[2][0]) / (gcdABCD * two);
			            if (Im < 0) { r *= -1; q *= -1; Re *= -1; Im *= -1; }
			            var check = 0;
			            for (var i = 0; i < found.length; i++) {
			                if (r == found[i][0] && Re == found[i][1] && Im == found[i][2] && q == found[i][3]) { check = 1; break; }
			            }
			            if (check == 0) {
			                found.push([r, Re, Im, q]); infoCount++;
			                infoArray.push([0, 0, 0, 0, 0, 0, 0.18, 0.6]);
			                var filter = document.createElementNS(NS, "filter");
			                filter.id = "infoFilter" + String(infoCount - 1);
			                filter.setAttribute("x", "-200%"); filter.setAttribute("y", "-200%");
			                filter.setAttribute("width", "500%"); filter.setAttribute("height", "500%");
			                filter.innerHTML = "<feGaussianBlur id='infoStdDev" + String(infoCount - 1) + "' in='SourceGraphic' stdDeviation='" + String(canvasWidth * 0.0058) + "' />";
			                canvas.insertBefore(filter, canvas.childNodes[0]);

			                if (r == 0) {
			                    if (Math.abs(Re) < sqrt * Im) {
			                        var y1 = canvasTop + (renderWidth + 1) * canvasWidth / 2, x1 = originX + (Re * (originY - y1) - q * scale * sqrt) / (sqrt * Im);
			                        var y2 = canvasTop + (1 - renderWidth) * canvasWidth / 2, x2 = originX + (Re * (originY - y2) - q * scale * sqrt) / (sqrt * Im);
			                    }
			                    else {
			                        var x1 = canvasLeft + (1 - renderWidth) * canvasWidth / 2, y1 = originY + (Im * sqrt * (originX - x1) - q * scale * sqrt) / Re;
			                        var x2 = canvasLeft + (renderWidth + 1) * canvasWidth / 2, y2 = originY + (Im * sqrt * (originX - x2) - q * scale * sqrt) / Re;
			                    }
			                    var newStroke = document.createElementNS(NS, "line");
			                    newStroke.setAttribute("x1", x1); newStroke.setAttribute("y1", y1);
			                    newStroke.setAttribute("x2", x2); newStroke.setAttribute("y2", y2);
			                    if (Im * Re != 0) {
			                        var newBlur = stroke.cloneNode(false);
			                        newBlur.setAttribute("stroke", "rgb(4,38,230)");
			                        newBlur.setAttribute("stroke-width", String(0.015 * canvasWidth));
			                    }
			                    else {
			                        var newBlur = document.createElementNS(NS, "rect");
			                        newBlur.setAttribute("fill", "rgb(4,38,230)");
			                        newBlur.setAttribute("stroke", "none");
			                        if (Im == 0) {
			                            newBlur.setAttribute("height", String(0.015 * canvasWidth));
			                            newBlur.setAttribute("width", String(3 * canvasWidth));
			                            newBlur.setAttribute("x", x1.toString());
			                            newBlur.setAttribute("y", String(y1 - 0.015 * canvasWidth / 2));
			                        }
			                        else {
			                            newBlur.setAttribute("width", String(0.015 * canvasWidth));
			                            newBlur.setAttribute("height", String(3 * canvasWidth));
			                            newBlur.setAttribute("y", y1.toString());
			                            newBlur.setAttribute("x", String(x1 - 0.015 * canvasWidth / 2));
			                        }
			                    }
			                    newStroke.setAttribute("stroke", "rgb(4,38,230)");
			                    newStroke.setAttribute("stroke-width", String(0.00192 * canvasWidth));
			                }
			                else {
			                    var newStroke = document.createElementNS(NS, "circle");
			                    newStroke.setAttribute("r", String(two * scale * Math.sqrt(currentPrin) / (2 * sqrt * Math.abs(r))));
			                    newStroke.setAttribute("cx", String(originX - scale * Im / (2 * r)));
			                    newStroke.setAttribute("cy", String(originY - scale * Re / (2 * sqrt * r)));
			                    newStroke.setAttribute("stroke", "rgb(4,38,230)");
			                    newStroke.setAttribute("fill", "none");
			                    var newBlur = newStroke.cloneNode(false);
			                    newBlur.setAttribute("stroke-width", String(0.015 * canvasWidth));
			                    newStroke.setAttribute("stroke-width", String(0.00192 * canvasWidth));
			                }
			                newBlur.setAttribute("filter", "url(#infoFilter" + String(infoCount - 1) + ")");
			                infoCircles.appendChild(newBlur); infoCircles.appendChild(newStroke);
			            }
			            var normZ = (zX * zX + d * zY * zY) / (two * two);
			            if (normZ != 0) {
			                zX *= gcd * zD; zY *= -1 * gcd * zD; zD = normZ;
			                gcd = getGcd((zX + (1 - two) * zY) / two, getGcd(zY, zD));
			                zX /= gcd; zY /= gcd; zD /= gcd;
			                setTimeout(function () {
			                    expand();
			                }, 800);
			            }
			            else {
			                canvas.addEventListener("mouseup", cfExpand);
			                canvasContain.addEventListener("mousemove", posDisplay);
			                canvasContain.addEventListener("mouseleave", posHide);
			                return;
			            }

			        }
			    }
			}

			function addSelect() {
				var oldStroke = stroke.childNodes[0], r = coords[0], x = coords[1], y = coords[2], i = coords[3];
			   var layer = arrangement.childNodes[r].childNodes[i];
			   if (layer.childNodes[0].hasAttribute("filter")) { var inc = 2; }
			   else { var inc = 1; }

			   if (r == 0) {
			   	var x1 = parseFloat(oldStroke.getAttribute("x1"));
			   	var x2 = parseFloat(oldStroke.getAttribute("x2"));
			    	var y1 = parseFloat(oldStroke.getAttribute("y1"));
			      var y2 = parseFloat(oldStroke.getAttribute("y2"));
			     	if (Math.abs(y1 - y2) < initWidth / 1000) {
			      	for (var j = inc - 1; j < layer.childNodes.length; j += inc) {
			         	var element = layer.childNodes[j];
			           	if(element.tagName != "text"){
			            	if (Math.abs(parseFloat(element.getAttribute("y1")) - y1) < initWidth / 1000) {
			               	if (element.style.visibility == "hidden") {
			                  	var k = 0;
			                     while (k < selectArray.length) {
			                     	if (selectArray[k][0] == r && selectArray[k][1] == x && selectArray[k][2] == y) {
			                        	checkSelect(k);
			                          	break;
			                       	}
			                      	k++;
			                		}
			              		}
			                 	else {
			                  	element.style.visibility = "hidden";
			                    	if (inc == 2) { layer.childNodes[j - 1].style.visibility = "hidden"; }
			                    	highlightSelected(j);
			                	}
			          		}
			       		}
			   		}
					}
			     	else {
			      	var slope = (x1 - x2) / (y1 - y2);
			        	for (var j = inc - 1; j < layer.childNodes.length; j += inc) {
			         	var element = layer.childNodes[j];
			         	if(element.tagName != "text"){
			           		var xx1 = parseFloat(element.getAttribute("x1"));
			           		var xx2 = parseFloat(element.getAttribute("x2"));
			           		var yy1 = parseFloat(element.getAttribute("y1"));
			           		var yy2 = parseFloat(element.getAttribute("y2"));
			            	if (Math.max(Math.abs(xx1 - x1 - slope * (yy1 - y1)), Math.abs(xx2 - x1 - slope * (yy2 - y1))) < initWidth / 1000) {
			              		if (element.style.visibility == "hidden") {
			                  	var k = 0;
			                   	while (k < selectArray.length) {
			                    		if (selectArray[k][0] == r && selectArray[k][1] == x && selectArray[k][2] == y) {
			                        	checkSelect(k);
			                          	break;
			                        }	    
			                      	k++;
			                 		}
			              		}
			                	else {
			                 		element.style.visibility = "hidden";
			                    	if (inc == 2) { layer.childNodes[j - 1].style.visibility = "hidden"; }
			                    	highlightSelected(j);
			                  }
			             	}
			         	}
			       	}
			 		}
			 	}
			 	else {
			   	var rad = parseFloat(oldStroke.getAttribute("r"));
			     	var centX = parseFloat(oldStroke.getAttribute("cx"));
			     	var centY = parseFloat(oldStroke.getAttribute("cy"));
			     	for (var j = 0; j < layer.childNodes.length; j += inc) {
			      	var element = layer.childNodes[j];
			      	if(element.tagName != "text"){
			         	if (Math.abs(parseFloat(element.getAttribute("cx")) - centX) < rad && Math.abs(parseFloat(element.getAttribute("cy")) - centY) < rad) {
			            	if (element.style.visibility == "hidden") {
			               	var k = 0;
			                 	while (k < selectArray.length) {
			                  	if (selectArray[k][0] == r && selectArray[k][1] == x && selectArray[k][2] == y) {
			                     	checkSelect(k);
			                      	break;
			                    	}
			                   	k++;
			               	}
			          		}
			             	else {
			               	element.style.visibility = "hidden";
			                	if (inc == 2) { layer.childNodes[j + 1].style.visibility = "hidden"; }
			                	//job talk
			                 	if(1 == 1){ highlightSelected(j); }
			                 	else{
										looper: for(var m = 0; m < circArray[i][r].length; m++){
											if(circArray[i][r][m][0] == y){
												for(var n = 1; n < circArray[i][r][m].length; n++){
													if(circArray[i][r][m][n] == x){
														circArray[i][r][m].splice(n, 1);
														break looper;													
													}
												}
											}									    
										}             	
			                 	}
			              	}
			           		break;
			       		}
			    		}
			 		}
				}

			    function highlightSelected(j) {
			    

			        var newStroke = oldStroke.cloneNode(false);
			        var newBlur = blur.childNodes[0].cloneNode(true);
			        var filter = document.createElementNS(NS, "filter");
			        filter.id = "selectFilter" + selectCount.toString();
			        filter.setAttribute("x", "-200%"); filter.setAttribute("y", "-200%");
			        filter.setAttribute("width", "500%"); filter.setAttribute("height", "500%");
			        filter.innerHTML = "<feGaussianBlur id='selectStdDev" + selectCount.toString() + "' in='SourceGraphic' stdDeviation='" + String(canvasWidth * (0.004 + 0.003 * styles[4][i][6])) + "' />";
			        canvas.insertBefore(filter, canvas.childNodes[0]);
			        newBlur.setAttribute("filter", "url(#selectFilter" + selectCount.toString() + ")");

			        newBlur.style.visibility = "visible"; newStroke.style.visibility = "visible";
			        selectCircles.appendChild(newBlur); selectCircles.appendChild(newStroke);

			        var tempArray = []; selectArray.push(tempArray);
			        for (var k = 0; k < 4; k++) { selectArray[selectCount].push(coords[k]); }
			        selectArray[selectCount].push(j); selectArray[selectCount].push(1);
			        selectArray[selectCount].push(styles[2][i][6]);
			        selectArray[selectCount].push(styles[4][i][6]);

			        for (var k = 0; k < selectCount; k++) { if (selectArray[k][5] == 1) { check(8, k); } }
			        var index = 0;
			        for (var k = 2; k < 5; k++) {
			            if (styles[k][total][7] > 1) { index = k; }
			            for (var l = 0; l < 11; l++) { styles[k][total][l] = styles[k][i][l]; }
			        }
			        if (styles[4][total][7] % 2 == 0) { styles[4][total][7] += 1; }
			        if (index > 0 && styles[index][total][7] < 2) { styles[index][total][7] += 2; }


			        var infoRow = document.createElement("tr");
			        infoRow.id = "row" + selectCount.toString();
			        var cell = document.createElement("td");
			        cell.style.width = "1.4em";
			        cell.style.paddingBottom = "0.5em";
			        var HTML = "<div class='checkBox' id='checkBox8," + selectCount.toString() + "' onclick='check(8," + selectCount.toString() + ")'>";
			        HTML += "<object class='checkmark' type='image/svg+xml' data='check.svg'></object></div>";
			        cell.innerHTML = HTML;
			        infoRow.appendChild(cell);
			        cell = document.createElement("td");
			        cell.style.paddingBottom = "0.5em";
			        cell.innerHTML = document.getElementById("infoDisplay").innerHTML;
			        infoRow.appendChild(cell); document.getElementById("infoTable").appendChild(infoRow);
			        ++selectCount; option(3, -2);
					
			    }
			}

			function checkSelect(i) {


			}

			function info() {
			    var infoButton = document.getElementById("info");
			    if (String(infoButton.classList).indexOf("stayActive") > -1) {
			        infoButton.classList.remove("stayActive"); selectLabelCount = 0;
			        while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
			        var i = 0; infoArray = [];
			        while (infoCount > 0) {
			            var element = canvas.childNodes[i];
			            if (element.id.indexOf("infoFilter") != -1) { canvas.removeChild(element); infoCount--; }
			            else { i++; }
			        }
			        while (infoLabels.lastChild) { infoLabels.removeChild(infoLabels.lastChild); }
			        while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
			        var body = document.getElementById("toggle7,7");
			        while (body.lastChild) { body.removeChild(body.lastChild); }
			        body = document.getElementById("toggle8,8");
			        while (body.lastChild) { body.removeChild(body.lastChild); }
			        while (notes.lastChild) { notes.removeChild(notes.lastChild); }
			        blur.style.visibility = "hidden";
			        stroke.style.visibility = "hidden";
			        var i = 0;
			        while (i < canvasContain.childNodes.length) {
			            var id = canvasContain.childNodes[i].id || "";
			            if (id.indexOf("infoNumber") != -1) { canvasContain.removeChild(canvasContain.childNodes[i]); }
			            else { i++; }
			        }
			        document.getElementById("transition").style.display = "none";
			        document.getElementById("infoDisplay").style.visibility = "hidden";
			        coords = [1, 0, 0, 1000]; infoArray = [];
			        canvas.removeEventListener("mousedown", getInfo);
			        canvasContain.removeEventListener("mousemove", infoHighlight);
			        canvas.removeEventListener("mouseleave", infoRemove);
			        canvas.addEventListener("dblclick", zoom);
			    }
			    else {
			        if (String(document.getElementById("cFrac").classList).indexOf("stayActive") > -1) { cFrac(); }
			        while (notes.lastChild) { notes.removeChild(notes.lastChild); }
			        infoButton.classList.add("stayActive");
			        canvas.removeEventListener("dblclick", zoom);
			        canvasContain.addEventListener("mousemove", infoHighlight);
			        canvas.addEventListener("mouseleave", infoRemove);
			        canvas.addEventListener("mousedown", getInfo);
			        var div = document.createElement("div");
			        div.style.paddingBottom = "0.2em";
			        div.innerHTML = "Data is of the form (&#119903;, &#119903;', &#119911;, &#124;&#124;&#120094;&#124;&#124;). Clicking near an intersection point, &#120572;/&#120573;, gives the corresponding matrix representation."
			        notes.appendChild(div);
			        var infoTable = document.createElement("table");
			        infoTable.id = "infoTable"; notes.appendChild(infoTable);

			        if (1 == 1) {
			            var label = document.createElementNS(NS, "g");
			            var rect = document.createElementNS(NS, "rect");
			            rect.id = "labels" + selectLabelCount.toString(); ++selectLabelCount;
			            rect.setAttribute("x", String(-0.011 * initWidth));
			            rect.setAttribute("y", String(-0.011 * initWidth));
			            rect.setAttribute("width", String(0.022 * initWidth));
			            rect.setAttribute("height", String(0.022 * initWidth));
			            rect.setAttribute("rx", String(0.004 * initWidth));
			            rect.setAttribute("ry", String(0.004 * initWidth));
			            rect.setAttribute("stroke", "rgb(0,0,0)"); rect.setAttribute("fill", "rgb(255,255,255)");
			            rect.setAttribute("stroke-width", String(0.0012 * initWidth));
			            label.appendChild(rect);
			            var text = document.createElementNS(NS, "text");
			            text.setAttribute("font-size", String(0.02 * initWidth));
			            text.setAttribute("fill", "rgb(0,0,0)");
			            text.setAttribute("x", "0"); text.setAttribute("y", String(0.007 * initWidth));
			            text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			            text.style.pointerEvents = "none"; text.innerHTML = "";
			            label.appendChild(text); selectLabels.appendChild(label);
			            label.setAttribute("transform", "translate(" + String(originX + scale * Math.PI) + "," + String(originY - scale * Math.sqrt(2)) + ") scale(" + String(canvasWidth / initWidth) + ")");

			        }
			    }
			}

			function infoRemove() {
			    blur.style.visibility = "hidden";
			    stroke.style.visibility = "hidden";
			    document.getElementById("infoDisplay").style.visibility = "hidden";
			    coords = [1, 0, 0, 1000];
			}

			function infoHighlight(e) {
			    var e = window.event || e, check = 0, target = e.target.id;
					
			    if (mouseDown == 0 && target.indexOf("ilabels") != -1) {
			        var index = target.split("s"); index = parseInt(index[1]);
			        for (var j = 0; j < 4; j++) {
			            if (coords[j] != infoArray[index][j]) {
			                check = 1; coords[j] = infoArray[index][j];
			            }
			        }
			    }
			    else {
			        var r = coords[0], i = coords[3], minDist = 1000;
			        var X = ((e.clientX - containLeft) * delta + canvasLeft - originX) / scale;
			        var Y = (originY - canvasTop - (e.clientY - containTop) * delta) / scale;
			        if (i < total) {
			            var principal = two * two * prin[i], sqrtp = Math.sqrt(principal) / sqrt;
			            if (r == 0) {
			                var y = coords[2], x = Math.floor(Math.sqrt(principal - y * y) / sqrt + 0.5);
			                minDist = Math.abs(x * X + coords[1] - y * Y / sqrt) / sqrtp - 4 * delta / initWidth;
			            }
			            else {
			                var centX = coords[1] / (2 * r), centY = coords[2] / (2 * r * sqrt), rad = sqrtp / (2 * r);
			                minDist = Math.abs(Math.sqrt((centY - Y) * (centY - Y) + (centX - X) * (centX - X)) - rad) - 4 * delta / initWidth;
			            }
			        }
			        for (var j = 0; j < total; j++) {
			            if (visible[j] == 1) {
			                var principal = two * two * prin[j], sqrtp = Math.sqrt(principal) / sqrt, jj = j % h;
			                
			                if(circArray[jj].length <= maxR){ circArray[jj].unshift([]);}
			                for (var y = 0; y < circArray[jj][0].length; y++) {
			                    if (circArray[jj][0][y].length > 1) {
			                        var yy = circArray[jj][0][y][0], n = 2;
			                        var xx = Math.floor(Math.sqrt(principal - yy * yy) / sqrt + 0.5);
			                        var oldDist = Math.abs(xx * X + circArray[jj][0][y][1] - yy * Y / sqrt) / sqrtp;
			                        while (n < circArray[jj][0][y].length) {
			                            var newDist = Math.abs(xx * X + circArray[jj][0][y][n] - yy * Y / sqrt) / sqrtp;
			                            if (oldDist < newDist) { break; }
			                            oldDist = newDist; n++
			                        }
			                        if (oldDist < minDist) {
			                            minDist = oldDist; check = 1;
			                            coords = [0, circArray[jj][0][y][n - 1], yy, j];
			                        }
			                    }
			                }
									
			                for (var r = 1; r <= maxR; r++) {
			                    var rad = sqrtp / (2 * r), y = 0;
			                    for (var y = 0; y < circArray[jj][r].length; y++) {
			                        if (circArray[jj][r][y].length > 1) {
			                        	
			                            var centY = circArray[jj][r][y][0] / (2 * r * sqrt);
			                            var dist = Math.abs(centY - Y);
			                            if (dist - rad < minDist) {
			                                dist *= dist;
			                                var centX = circArray[jj][r][y][1] / (2 * r), x = 2;
			                                var oldDist = Math.abs(Math.sqrt(dist + (centX - X) * (centX - X)) - rad);
			                                while (x < circArray[jj][r][y].length) {
			                                    centX = circArray[jj][r][y][x] / (2 * r);
			                                    var newDist = Math.abs(Math.sqrt(dist + (centX - X) * (centX - X)) - rad);
			                                    if (oldDist < newDist) { break; }
			                                    oldDist = newDist; x++;
			                                }
			                                if (oldDist < minDist) {
			                                    minDist = oldDist; check = 1;
			                                    coords = [r, circArray[jj][r][y][x - 1], circArray[jj][r][y][0], j];
			                                }
			                                
			                            }
			                        }
			                    }
			                }
			            }
			        }
			        
			    }

			    if (check == 1) {

			        var r = coords[0], i = coords[3], principal = two * two * prin[i], y = coords[2];
			        var infoDisplay = document.getElementById("infoDisplay");
			        stdDevHL.setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * styles[4][i][6])));

			        if (r == 0) {
			            var q = coords[1], x = Math.floor(Math.sqrt(principal - y * y) / sqrt + 0.5);

			            if (Math.abs(y) < sqrt * x) {
			                var y1 = canvasTop + 2 * canvasWidth, x1 = originX + (y * (originY - y1) - q * scale * sqrt) / (sqrt * x);
			                var y2 = canvasTop - canvasWidth, x2 = originX + (y * (originY - y2) - q * scale * sqrt) / (sqrt * x);
			            }
			            else {
			                var x1 = canvasLeft - canvasWidth, y1 = originY + (x * sqrt * (originX - x1) - q * scale * sqrt) / y;
			                var x2 = canvasLeft + 2 * canvasWidth, y2 = originY + (x * sqrt * (originX - x2) - q * scale * sqrt) / y;
			            }

			            var thick = 0.005 * canvasWidth * (0.05 + 3 * styles[4][i][6]);

			            if (x == 0 || y == 0) {
			                var newBlur = document.createElementNS(NS, "rect");
                            if (x == 0) {
                                newBlur.setAttribute("x", x1.toString());
                                newBlur.setAttribute("y", String(y1 - thick / 2));
                                newBlur.setAttribute("height", thick.toString());
                                newBlur.setAttribute("width", String(3 * canvasWidth));
			                }
			                else {
                                newBlur.setAttribute("x", String(x1 - thick / 2));
                                newBlur.setAttribute("y", y2.toString());
                                newBlur.setAttribute("width", thick.toString());
                                newBlur.setAttribute("height", String(3 * canvasWidth));
			                }
                            newBlur.setAttribute("fill", "rgb(" + styles[4][i][8] + "," + styles[4][i][9] + "," + styles[4][i][10] + ")");
                            newBlur.setAttribute("stroke", "none");
			            }
                        else {
                            var newBlur = document.createElementNS(NS, "line");
                            newBlur.setAttribute("x1", x1); newBlur.setAttribute("y1", y1);
                            newBlur.setAttribute("x2", x2); newBlur.setAttribute("y2", y2);
                            newBlur.setAttribute("stroke-width", thick.toString());
                            newBlur.setAttribute("stroke", "rgb(" + styles[4][i][8] + "," + styles[4][i][9] + "," + styles[4][i][10] + ")");
			            }

			            var newStroke = document.createElementNS(NS, "line");
			            newStroke.setAttribute("x1", x1); newStroke.setAttribute("y1", y1);
			            newStroke.setAttribute("x2", x2); newStroke.setAttribute("y2", y2);
			            newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][i][6])));
			            newStroke.setAttribute("stroke", "rgb(" + styles[2][i][8] + "," + styles[2][i][9] + "," + styles[2][i][10] + ")");

			            var entry = getEntry((y - (two - 1) * x) / two, x);
			            infoDisplay.innerHTML = "(0, " + q + ", " + entry + ", " + principal + ")";
			            var displayWidth = infoDisplay.offsetWidth, displayHeight = infoDisplay.offsetHeight;
			            infoDisplay.style.left = String(Math.max(0,Math.min(containWidth - displayWidth,((x1 + x2 - 2 * canvasLeft) / delta - displayWidth) / 2))) + "px";
			            infoDisplay.style.top = String(Math.max(0,Math.min(containWidth - displayHeight,((y1 + y2 - 2 * canvasTop) / delta - displayHeight) / 2))) + "px";
			        }
			        else {
			            var x = -1 * coords[1], q = (y * y + d * x * x - principal) / (4 * d * r);
			            var centX = originX - scale * x / (2 * r);
			            var centY = originY - scale * y / (2 * r * sqrt);
			            var rad = scale * Math.sqrt(principal) / (2 * r * sqrt);
			            var newBlur = document.createElementNS(NS, "circle");
			            newBlur.setAttribute("cx", centX);
			            newBlur.setAttribute("cy", centY);
			            newBlur.setAttribute("r", rad);
			            newBlur.setAttribute("fill", "none");
			            newBlur.setAttribute("stroke-width", String(0.005 * canvasWidth * (0.05 + 3 * styles[4][i][6])));
			            newBlur.setAttribute("stroke", "rgb(" + styles[4][i][8] + "," + styles[4][i][9] + "," + styles[4][i][10] + ")");
			            var newStroke = document.createElementNS(NS, "circle");
			            newStroke.setAttribute("cx", centX);
			            newStroke.setAttribute("cy", centY);
			            newStroke.setAttribute("r", rad);
			            newStroke.setAttribute("fill", "none");
			            newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][i][6])));
			            newStroke.setAttribute("stroke", "rgb(" + styles[2][i][8] + "," + styles[2][i][9] + "," + styles[2][i][10] + ")");

			            var entry = getEntry((y - (two - 1) * x) / two, x); principal /= (two * two);
			            infoDisplay.innerHTML = "(" + r + ", " + q + ", " + entry + ", " + principal + ")";
			            var displayWidth = infoDisplay.offsetWidth, displayHeight = infoDisplay.offsetHeight;
			            infoDisplay.style.left = String(Math.max(0, Math.min(containWidth - displayWidth, (centX - canvasLeft) / delta - displayWidth / 2))) + "px";
			            infoDisplay.style.top = String(Math.max(displayHeight, Math.min(containWidth, (centY - rad - canvasTop) / delta)) - displayHeight) + "px";
			        }

			        blur.childNodes[0].replaceWith(newBlur);
			        stroke.childNodes[0].replaceWith(newStroke);
			        blur.style.visibility = "visible";
			        stroke.style.visibility = "visible";
			        infoDisplay.style.visibility = "visible";
			    }
			}

			function getInfo(e) {

			    var e = window.event || e, target = e.target;
			    var inX = outX = e.clientX, inY = outY = e.clientY;
			    if (target.id.indexOf("ilabels") != -1) {
			        e.stopPropagation();
			        if (infoCheck == 1) { canvas.removeEventListener("mouseup", completeInfo); infoCheck = 0; }
			        var label = target.parentNode, index = target.id.split("s"); index = parseInt(index[1]), moveCheck = 0;
			        var transform = label.getAttribute("transform");
			        var startX = parseFloat(transform.substring(transform.indexOf("(") + 1, transform.indexOf(",")));
			        var startY = parseFloat(transform.substring(transform.indexOf(",") + 1, transform.indexOf(")")));
			        transform = transform.split(" ");

			        var oldBlur = infoCircles.childNodes[2 * index], oldStroke = infoCircles.childNodes[2 * index + 1];
			        if (oldBlur.style.visibility != "hidden") {
			            for (var j = 0; j < infoArray.length; j++) {
			                var check = 1;
			                if (j != index) {
			                    check = 0;
			                    for (var k = 0; k < 4; k++) {
			                        if (infoArray[j][k] != coords[k]) { check = 1; break; }
			                    }
			                }
			                if (check == 0) {
			                    infoCircles.childNodes[2 * j].style.visibility = "visible";
			                    infoCircles.childNodes[2 * j + 1].style.visibility = "visible";
			                    break;
			                }
			            }
			            oldBlur.style.visibility = "hidden";
			            oldStroke.style.visibility = "hidden";
			        }
			        canvas.addEventListener("mousemove", dragInfo);
			        document.addEventListener("mouseup", stopInfo);

			        function dragInfo(e) {
			            e = window.event || e; outX = e.clientX; outY = e.clientY;
			            if (Math.abs(inX - outX) > 1 || Math.abs(inY - outY) > 1) {
			                moveCheck = 1;
			                var x = startX + (outX - inX) * delta, y = startY + (outY - inY) * delta;
			                label.setAttribute("transform", "translate(" + x.toString() + "," + y.toString() + ") " + transform[1]);
			                label.childNodes[1].setAttribute("fill", stroke.childNodes[0].getAttribute("stroke"));
			            }
			        }

			        function stopInfo() {

			            canvas.removeEventListener("mousemove", dragInfo);
			            document.removeEventListener("mouseup", stopInfo);
			            if (moveCheck == 1) { postInfo(index + 1); }
			            else {
			                infoLabels.removeChild(label); infoArray.splice(index, 1);
			                infoCircles.removeChild(oldBlur); infoCircles.removeChild(oldStroke);
			                for (var j = 7; j < 9; j++) {
			                    var body = document.getElementById("toggle" + j.toString() + "," + j.toString());
			                    body.removeChild(body.lastChild);
			                }
			                var infoTable = document.getElementById("infoTable");
			                var rows = infoTable.getElementsByClassName("infoRow");
			                var newCells = rows[index].getElementsByTagName("td");
			                for (var j = index + 1; j < infoCount; j++) {
			                    var oldCells = newCells;
			                    newCells = rows[j].getElementsByTagName("td");
			                    oldCells[1].innerHTML = newCells[1].innerHTML;
			                    oldCells[3].innerHTML = newCells[3].innerHTML;
			                    var oldLabel = document.getElementById("ilabels" + j.toString());
			                    oldLabel.id = "ilabels" + String(j - 1);
			                    oldLabel.parentNode.childNodes[1].innerHTML = j.toString();
			                }
			                --infoCount; infoTable.removeChild(rows[infoCount]);
			                if (infoCount < 2) { document.getElementById("transition").style.display = "none"; }
			                else {
			                    var checkOption = 0;
			                    var header7 = document.getElementById("header7"), header8 = document.getElementById("header8");
			                    var data7 = parseInt(header7.getAttribute("data-value")), data8 = parseInt(header8.getAttribute("data-value"));
			                    if (data7 == index || data8 == index) { checkOption = 1; }
			                    if (data7 > index) {
			                        checkOption = 1;
			                        header7.setAttribute("data-value", String(data7 - 1));
			                        header7.innerHTML = document.getElementById("option7," + String(data7 - 1)).innerHTML;
			                    }
			                    if (data8 > index) { checkOption = 1; }
			                    if (checkOption == 1) { option(8, data8 - 1); }
			                }
			            }
			        }
			    }
			    else { canvas.addEventListener("mouseup", completeInfo); infoCheck = 1; }

			    function completeInfo(e) {
			        if (infoCheck == 1) {

			            e = window.event || e; e.stopImmediatePropagation();
			            canvas.removeEventListener("mouseup", completeInfo); infoCheck = 0;
			            outX = e.clientX; outY = e.clientY;
			            var tempArray = [];
			            for (var j = 0; j < 16; j++) { tempArray.push(0); }
			            infoArray.push(tempArray);

			            for (var j = 7; j < 9; j++) {
			                var body = document.getElementById("toggle" + j.toString() + "," + j.toString());
			                var row = document.createElement("tr");
			                var HTML = "<td id='td" + j.toString() + "," + infoCount.toString() + "' onclick='option(" + j.toString() + "," + infoCount.toString() + ")' onmouseover='highlight(" + j.toString() + "," + infoCount.toString() + ",0)' onmouseout='highlight(" + j.toString() + "," + infoCount.toString() + ",1)'>";
			                HTML += "<div id='option" + j.toString() + "," + infoCount.toString() + "' style='width:2.5em;height:1.3em;'>&#x1d440;<sub class='subScript'>" + String(infoCount + 1) + "</sub></div></td>";
			                row.innerHTML = HTML; body.appendChild(row);
			            }
			            var infoRow = document.createElement("tr");
			            infoRow.className = "infoRow";
			            infoRow.style.paddingBottom = "1em";
			            for (var j = 0; j < 4; j++) {
			                var cell = document.createElement("td");
			                infoRow.appendChild(cell);
			            }
			            document.getElementById("infoTable").appendChild(infoRow);

			            var label = document.createElementNS(NS, "g");
			            if(infoCount == 0){
			            	var rect = document.createElementNS(NS, "rect");
			            	rect.id = "ilabels" + infoCount.toString(); ++infoCount;
			            	rect.setAttribute("x", String(-0.018 * initWidth));
			            	rect.setAttribute("y", String(-0.018 * initWidth));
			            	rect.setAttribute("width", String(0.036 * initWidth));
			            	rect.setAttribute("height", String(0.036 * initWidth));
			            	rect.setAttribute("rx", String(0.006 * initWidth));
			            	rect.setAttribute("ry", String(0.006 * initWidth));
			            	rect.setAttribute("stroke", "rgb(150,150,150)");
			            	rect.setAttribute("stroke-width", String(0.0014 * initWidth));
			            	rect.setAttribute("fill", "rgb(255,255,255)");

			            	if (1 == 0) {
			                	if (infoCount == 1 || infoCount == 2 || infoCount == 5 || infoCount == 7 || infoCount == 14) {
			                    rect.setAttribute("fill", "rgb(254,172,87)");
			                	}
			                	if (infoCount == 6 || infoCount == 9 || infoCount == 10 || infoCount == 12 || infoCount == 13) {
			                    rect.setAttribute("fill", "rgb(218,174,221)");
			               	 }
			                	if (infoCount == 3 || infoCount == 4 || infoCount == 8 || infoCount == 11 || infoCount == 15 || infoCount == 16 || infoCount == 17) {
			                    rect.setAttribute("fill", "rgb(157,228,182)");
			                	}
			            	}
			            	label.appendChild(rect);
			            	var text = document.createElementNS(NS, "text");
			            	text.setAttribute("font-size", String(0.03 * initWidth));
			            	text.setAttribute("fill", stroke.childNodes[0].getAttribute("stroke"));
			            	text.setAttribute("x", "0"); text.setAttribute("y", String(0.0105 * initWidth));
			            	text.setAttribute("text-anchor", "middle"); text.setAttribute("font-weight", "bold");
			            	text.style.pointerEvents = "none";
			            	text.innerHTML = String(infoCount);

			            	if (1 == 0) {
			                	if (infoCount < 3) {
			                    rect.setAttribute("fill", "rgb(232,138,142)");
			                	}
			                	if (infoCount == 3) {
			                    rect.setAttribute("fill", "rgb(218,174,221)");
			                    text.innerHTML = "";
			                	}
			                	if (infoCount > 3) {
			                    rect.setAttribute("fill", "rgb(181,202,253)");
			                    text.innerHTML = String(infoCount - 3);
			                	}
			            	}
			            	if(1 == 0){ label.appendChild(text); }
			            }
			            else{
			            	var dot = document.createElementNS(NS, "circle");
			            	dot.id = "ilabels" + infoCount.toString(); ++infoCount;
			            	dot.setAttribute("cx", "0");
			            	dot.setAttribute("cy", "0");
			            	dot.setAttribute("r", String(0.01 * initWidth));
			            	dot.setAttribute("stroke", "none");
			            	dot.setAttribute("fill", "rgba(166,25,25,1)");
			            	label.appendChild(dot);
			            }
			            infoLabels.appendChild(label);
			            postInfo(infoCount);
			        }
			    }

			    function postInfo(n) {
			        var cells = document.getElementById("infoTable").getElementsByClassName("infoRow")[n - 1].getElementsByTagName("td");
			        cells[0].innerHTML = n + ".&nbsp;";
			        cells[1].innerHTML = document.getElementById("infoDisplay").innerHTML + ",&nbsp;&nbsp;";
			        cells[2].innerHTML = "&#x1d440;<sub class='subScript'>" + n.toString() + "</sub> =&nbsp;";
			        for (var j = 0; j < 4; j++) { infoArray[n - 1][j] = coords[j]; }
			        var r = coords[0], y = coords[2], i = coords[3];
			        if (i - total + h >= twoTor && (i - total + h - twoTor) % 2 == 1) { i--; }
			        var torsion = tor[i], principal = two * two * prin[i], s = dets[i][0], t = dets[i][1];
			        var norm = parseInt(Math.sqrt((s * s + t * t * d) / principal));
			        if ((y - torsion) % (2 * d / two) == 0) { torsion *= -1; }
			        else { s *= -1; t *= -1; }
			        infoArray[n - 1][4] = s; infoArray[n - 1][5] = t;
			        infoArray[n - 1][6] = styles[2][i][6]; infoArray[n - 1][7] = styles[4][i][6];
                    outX = ((outX - containLeft) * delta + canvasLeft - originX) / scale;
                    outY = (originY - (outY - containTop) * delta - canvasTop) / (sqrt * scale);
                    var minDist = canvasWidth * canvasWidth / (scale * scale), sqrtp = Math.sqrt(principal) / sqrt;
                    if (r == 0) {
                        var q = coords[1], x = Math.floor(Math.sqrt(principal - y * y) / sqrt + 0.5);
                        if (q == 0) {
                            if (x == 0 || y == 0) { var alp1 = Math.max(Math.abs(x), Math.abs(y)); }
                            else {
                                var gcdMax = Math.min(Math.abs(x), Math.abs(y)), alp1 = 1;
                                for (var j = 2; j <= gcdMax; j++) { if (x % j == 0 && y % j == 0) { alp1 = j; } }
                            }
                        }
                        else {
                            if (x == 0 || y == 0) { var gcdMax = Math.min(Math.abs(q), Math.max(Math.abs(x), Math.abs(y))); }
                            else { var gcdMax = Math.min(Math.abs(q), Math.abs(x), Math.abs(y)); }
                            var alp1 = 1;
                            for (var j = 2; j <= gcdMax; j++) { if (q % j == 0 && x % j == 0 && y % j == 0) { alp1 = j; } }
                        }
                        var alp2 = bet1 = bet2 = gam1 = 0, gam2 = two * q / alp1, del1 = two * y / alp1, del2 = two * x / alp1; alp1 *= two;

                        var intX = gam2 * del2 * d, intY = gam2 * del1, intDen = del1 * del1 + d * del2 * del2;
                        for (var rr = 1; rr <= maxR; ++rr) {
                            var minY = Math.ceil(2 * sqrt * rr * (originY - canvasTop - canvasWidth) / scale - sqrt * sqrtp);
                            var maxY = Math.floor(2 * sqrt * rr * (originY - canvasTop) / scale + sqrt * sqrtp);
                            var minX = Math.ceil(2 * rr * (canvasLeft - originX) / scale - sqrtp);
                            var maxX = Math.floor(2 * rr * (canvasLeft - originX + canvasWidth) / scale + sqrtp);
                            var yy = torsion - 2 * d * Math.floor(two * (torsion - minY) / (2 * d) + 0.5) / two;
                            while (yy <= maxY) {
                                for (var xx = minX; xx <= maxX; xx++) {
                                    var dist = Math.abs(2 * d * q * rr - y * yy + d * x * xx);
                                    if (dist == principal && (d * xx * xx + yy * yy - principal) % (4 * d * rr) == 0) {
                                        var XX = xx * y * y + x * y * yy - 2 * d * x * q * rr, YY = 2 * q * y * rr + x * xx * y + x * x * yy, DD = 2 * rr * principal;
                                        dist = (outX - XX / DD) * (outX - XX / DD) + d * (outY - YY / DD) * (outY - YY / DD);
                                        if (dist < minDist) { minDist = dist; intX = XX; intY = YY; intDen = DD; }
                                    }
                                }
                                yy += 2 * d / two;
                            }
                        }
                    }
                    else{
                        y = two * (norm * coords[2] - s) / (2 * d);
                        var x = (t + norm * coords[1]) / 2 - (two - 1) * y / two;
                        s = (s - (two - 1) * t) / two;
                        var del2 = 1, tau = ((two - 1) * (two - 1) + d) / (two * two);
                        if (x == 0 && y == 0) { del2 = r; }
                        else {
                            if (x == 0 || y == 0) { var gcdMax = Math.min(r, Math.max(Math.abs(x), Math.abs(y))); }
                            else { var gcdMax = Math.min(r, Math.abs(x), Math.abs(y)); }
                            for (var j = 2; j <= gcdMax; j++) { if (r % j == 0 && x % j == 0 && y % j == 0) { del2 = j; } }
                        }
                        var alp2 = y / del2, alp1 = x / del2, bet1 = two * norm * r / del2;
                        for (var j = 0; j < norm * r; j++) {
                            if ((j * y + del2 * (x - t + (two - 1) * y)) % (norm * r) == 0 && (j * x - del2 * (y * tau + s)) % (norm * r) == 0) { var del1 = j; break; }
                        }
                        var gam1 = (del1 * x - del2 * (y * tau + s)) / (norm * r), gam2 = (del1 * y + del2 * (x - t + (two - 1) * y)) / (norm * r);
                        alp1 = two * (alp1 + alp2) - alp2; gam1 = two * (gam1 + gam2) - gam2; del1 = two * (del1 + del2) - del2;
                        x = coords[1]; y = coords[2];
                        var intX = alp1, intY = alp2, intDen = bet1;
                        for (var rr = 1; rr <= maxR; ++rr) {
                            var minY = Math.ceil(2 * sqrt * rr * (originY - canvasTop - canvasWidth) / scale - sqrt * sqrtp);
                            var maxY = Math.floor(2 * sqrt * rr * (originY - canvasTop) / scale + sqrt * sqrtp);
                            var minX = Math.ceil(2 * rr * (canvasLeft - originX) / scale - sqrtp);
                            var maxX = Math.floor(2 * rr * (canvasLeft - originX + canvasWidth) / scale + sqrtp);
                            var yy = torsion - 2 * d * Math.floor(two * (torsion - minY) / (2 * d) + 0.5) / two;
                            while (yy <= maxY) {
                                for (var xx = minX; xx <= maxX; xx++) {
                                    var dist = d * (x * rr - xx * r) * (x * rr - xx * r) + (y * rr - yy * r) * (y * rr - yy * r);
                                    if (dist == principal * (r + rr) * (r + rr) && (d * xx * xx + yy * yy - principal) % (4 * d * rr) == 0) {
                                        var XX = x + xx, YY = (y + yy) / d, DD = 2 * (r + rr);
                                        dist = (outX - XX / DD) * (outX - XX / DD) + d * (outY - YY / DD) * (outY - YY / DD);
                                        if (dist < minDist) { minDist = dist; intX = XX; intY = YY; intDen = DD; }
                                    }
                                }
                                yy += 2 * d / two;
                            }
                        }
                    }

                    var m = del1 * intY + del2 * intX - gam2 * intDen, l = alp2 * intDen - bet1 * intY;
                    if (m == 0 && l == 0) { m = del1 * intX - d * del2 * intY - gam1 * intDen; l = alp1 * intDen - bet1 * intX; }
                    if (m == 0 || l == 0) { var max = Math.max(Math.abs(m), Math.abs(l)); m /= max; l /= max; }
                    else {
                        var gcd = 1
                        for (var j = 2; j <= Math.min(Math.abs(m), Math.abs(l)) ; j++) {
                            if (m % j == 0 && l % j == 0) { gcd = j; }
                        }
                        m /= gcd; l /= gcd;
                    }
                    var p = Math.floor(l / 2);
                    if (l == 0) { var o = 0; p = m; }
                    else {
                        while (true) {
                            if ((m * p - 1) % l == 0) { var o = (m * p - 1) / l; break; }
                            p--;
                        }
                    }
                    var entries = [alp1 * m + gam1 * l, alp2 * m + gam2 * l, alp1 * o + gam1 * p, alp2 * o + gam2 * p, bet1 * m + del1 * l, del2 * l, bet1 * o + del1 * p, del2 * p];
                    if (d == 1 && Math.abs(entries[0]) < Math.abs(entries[1])) {
                        for (var j = 0; j < 4; j++) {
                            if (j % 2 == 0) { var k = 1; }
                            else { var k = -1; }
                            var temp = entries[2 * j];
                            entries[2 * j] = entries[2 * j + 1] * k;
                            entries[2 * j + 1] = -1 * k * temp;
                        }
                    }
                    var j = 0;
                    while (true) {
                        if (entries[j] != 0) {
                            if (entries[j] < 0) { for (var k = j; k < 8; k++) { entries[k] *= -1; } }
                            break;
                        }
                        j++; if (j == 2) { j += 2; }
                    }
                    if (r == 0 && two == 2) {
                        var check = 0;
                        var tempMat = [];
                        for (var j = 0; j < 4; j++) {
                            tempMat.push((entries[2 * j] - entries[2 * j + 1]) / 2);
                            tempMat.push(entries[2 * j + 1]);
                        }
                        for (var j = 0; j < 2; j++) { if (tempMat[j] % 2 != 0) { check = 1; } }
                        for (var j = 4; j < 6; j++) { if (tempMat[j] % 2 != 0) { check = 1; } }
                        if (check == 0) {
                            for (var j = 0; j < 2; j++) { entries[j] /= 2; }
                            for (var j = 4; j < 6; j++) { entries[j] /= 2; }
                        }
                        else {
                            for (var j = 2; j < 4; j++) { entries[j] /= 2; }
                            for (var j = 6; j < 8; j++) { entries[j] /= 2; }
                        }
                    }

                    for (var j = 0; j < 8; j++) { infoArray[n - 1][j + 8] = entries[j]; }

                    var matrix = document.createElement("table");
                    matrix.className = "matrix";
                    var row = document.createElement("tr");
                    row.style.paddingBottom = "0.2em";
                    for (var j = 0; j < 4; j++) {
                        if (j == 0 || j == 2) {
                            cell = document.createElement("td");
                            cell.style.width = "0.3em";
                            cell.style.borderTop = "1px solid black";
                            row.appendChild(cell);
                        }
                        if (j == 2) {
                            matrix.appendChild(row)
                            row = document.createElement("tr");
                            cell = document.createElement("td");
                            cell.style.width = "0.3em";
                            cell.style.borderBottom = "1px solid black";
                            row.appendChild(cell);
                        }

                        cell = document.createElement("td");
                        cell.innerHTML = getEntry((entries[2 * j] - (two - 1) * entries[2 * j + 1]) / two, entries[2 * j + 1]);
                        if (j == 0 || j == 2) { cell.style.paddingRight = "0.3em"; }
                        row.appendChild(cell);

                        if (j == 3) {
                            cell = document.createElement("td");
                            cell.style.width = "0.3em";
                            cell.style.borderBottom = "1px solid black";
                            row.appendChild(cell);
                            matrix.appendChild(row);
                        }
                    }

                    intX = originX + scale * intX / intDen;
                    intY = originY - scale * sqrt * intY / intDen;
                    var label = document.getElementById("ilabels" + String(n - 1)).parentNode;
                    label.setAttribute("transform", "translate(" + intX.toString() + "," + intY.toString() + ") scale(" + String(canvasWidth / initWidth) + ")");

                    var newStroke = stroke.childNodes[0].cloneNode(false);
                    var newBlur = blur.childNodes[0].cloneNode(false);
                    var filter = document.createElementNS(NS, "filter");
                    filter.id = "infoFilter" + String(infoCount - 1);
                    filter.setAttribute("x", "-200%"); filter.setAttribute("y", "-200%");
                    filter.setAttribute("width", "500%"); filter.setAttribute("height", "500%");
                    filter.innerHTML = "<feGaussianBlur id='infoStdDev" + String(infoCount - 1) + "' in='SourceGraphic' stdDeviation='" + String(canvasWidth * (0.004 + 0.003 * styles[4][coords[3]][6])) + "' />";
                    canvas.insertBefore(filter, canvas.childNodes[0]);
                    newBlur.setAttribute("filter", "url(#infoFilter" + String(infoCount - 1) + ")");
                    newBlur.style.visibility = "hidden";
                    newStroke.style.visibility = "hidden";

                    for (var j = 0; j < infoArray.length; j++) {
                        var check = 1;
                        if (j != n - 1) {
                            check = 0;
                            for (var k = 0; k < 4; k++) {
                                if (infoArray[j][k] != coords[k]) { check = 1; break; }
                            }
                        }
                        if (check == 0) {
                            newBlur.style.visibility = "hidden";
                            newStroke.style.visibility = "hidden";
                            break;
                        }
                    }

                    if (2 * n > infoCircles.childNodes.length) {
                        infoCircles.appendChild(newBlur);
                        infoCircles.appendChild(newStroke);
                        cells[3].appendChild(matrix);
                        if (n > 1) { option(8, n - 1); }
                        notes.scrollTop = notes.scrollHeight;
                    }
                    else {
                        infoCircles.childNodes[2 * n - 2].replaceWith(newBlur);
                        infoCircles.childNodes[2 * n - 1].replaceWith(newStroke);
                        cells[3].childNodes[0].replaceWith(matrix);
                        if (infoCount > 1) {
                            if (document.getElementById("header7").getAttribute("data-value") == String(n - 1)) { option(7, n - 1); }
                            if (document.getElementById("header8").getAttribute("data-value") == String(n - 1)) { option(8, n - 1); }
                        }
                    }
			    }
			}

			function matrixMult(matrix1, matrix2) {
			    var alp1 = (matrix1[0] * matrix2[0] + matrix1[2] * matrix2[4] - d * (matrix1[1] * matrix2[1] + matrix1[3] * matrix2[5])) / two;
			    var gam1 = (matrix1[0] * matrix2[2] + matrix1[2] * matrix2[6] - d * (matrix1[1] * matrix2[3] + matrix1[3] * matrix2[7])) / two;
			    var bet1 = (matrix1[4] * matrix2[0] + matrix1[6] * matrix2[4] - d * (matrix1[5] * matrix2[1] + matrix1[7] * matrix2[5])) / two;
			    var del1 = (matrix1[4] * matrix2[2] + matrix1[6] * matrix2[6] - d * (matrix1[5] * matrix2[3] + matrix1[7] * matrix2[7])) / two;
			    var alp2 = (matrix1[0] * matrix2[1] + matrix1[1] * matrix2[0] + matrix1[2] * matrix2[5] + matrix1[3] * matrix2[4]) / two;
			    var gam2 = (matrix1[0] * matrix2[3] + matrix1[1] * matrix2[2] + matrix1[2] * matrix2[7] + matrix1[3] * matrix2[6]) / two;
			    var bet2 = (matrix1[4] * matrix2[1] + matrix1[5] * matrix2[0] + matrix1[6] * matrix2[5] + matrix1[7] * matrix2[4]) / two;
			    var del2 = (matrix1[4] * matrix2[3] + matrix1[5] * matrix2[2] + matrix1[6] * matrix2[7] + matrix1[7] * matrix2[6]) / two;

			    return ([alp1, alp2, gam1, gam2, bet1, bet2, del1, del2]);
			}

			function getEntry(i, j) {
			    if (i == 0) {
			        if (j == 1) { var entry = "&#x1D70F;"; }
			        if (j == -1) { var entry = "-&#x1D70F;"; }
			        if (j == 0) { var entry = "0"; }
			        if (j != 0 && j != 1 && j != -1) { var entry = j.toString() + "&#x1D70F;"; }
			    }
			    else {
			        var entry = i.toString();
			        if (j > 0) {
			            if (j == 1) { entry += "+&#x1D70F;"; }
			            else { entry += "+" + j.toString() + "&#x1D70F;"; }
			        }
			        if (j < 0) {
			            if (j == -1) { entry += "-&#x1D70F;"; }
			            else { entry += "-" + String(-1 * j) + "&#x1D70F;"; }
			        }
			    }
			    return entry;
			}

			function colorPick(e) {

			    var e = window.event || e;
				var element = parseInt(document.getElementById("header3").getAttribute("data-value")), j = -1;
				for(var i = 2; i < 5; i++){ if(styles[i][element][7] > 1){ j = i; } }
				if(j == -1){
					element = 0; for(var i = 0; i < 2; i++){ if(styles[i][element][7] > 1){ j = i; } }
				}
				var y = e.clientY + window.pageYOffset, x = e.clientX;
				var red, blue, green, outX, outY = false;
				var rgbInput = document.getElementById("rgb" + j.toString()), alpha = styles[j][element][6];
				var black = styles[j][element][3], barPick = document.getElementById("barPick");
				var swatch = document.getElementById("swatch" + j.toString());
				var alphaPick = document.getElementById("alphaPick"), blurPick = document.getElementById("blurPick");
				var svg = document.getElementById("colorPick");
				var svgLeft = svg.offsetLeft, svgTop = svg.offsetTop, ratio = svg.offsetWidth;

				if (e.target.id == "colorWheel") {
				    ratio = 158.5 / ratio;
					++zoomPan;
					var colArray = [[1,0],[1,-1],[0,0],[0,0],[0,1],[1,0]];
					var stopBlack = document.getElementById("stopBlack");
					var wheelPick = document.getElementById("wheelPick");
					colorWheel(x,y);

					function colorWheel(x,y){
					    x = ratio * (x - svgLeft);
						y = ratio * (y - svgTop);
						var rad = Math.sqrt((x - 68) * (x - 68) + (y - 66) * (y - 66));
						outX = Math.min(64,rad) * (x - 68) / Math.max(0.1,rad) + 68;
						outY = Math.min(64, rad) * (y - 66) / Math.max(0.1, rad) + 66;
						wheelPick.setAttribute("cx",outX);
						wheelPick.setAttribute("cy",outY);
						var rad = Math.min(1, Math.sqrt((68 - outX) * (68 - outX) + (66 - outY) * (66 - outY)) / 66);
						var theta = Math.PI / 2;
						if(outX == 68 && outY > 66){ theta *= -1; }
						if(outX != 68){
							theta = Math.atan((66 - outY) / (outX - 68));
							if(outX < 68){
								if(outY > 66){ theta -= Math.PI; }
								else{ theta += Math.PI; }
							}
						}
						theta = theta / (2 * Math.PI) + 0.5;
						let i = 0;
						while(i < 5){ if(i + 1 > 6 * theta){ break; } i++; }
						theta = Math.min(1, 6 * theta - i);
						red = Math.floor(255 *(1 + rad * (colArray[i][0] + colArray[i][1] * theta - 1)) + 0.5);
						green = Math.floor(255 *(1 + rad * (colArray[(i + 2) % 6][0] + colArray[(i + 2) % 6][1] * theta - 1)) + 0.5);
						blue = Math.floor(255 *(1 + rad * (colArray[(i + 4) % 6][0] + colArray[(i + 4) % 6][1] * theta - 1)) + 0.5);
						var rgb = "rgb(" + red.toString() + "," + green.toString() + "," + blue.toString() + ")";
						stopBlack.style.stopColor = rgb; wheelPick.setAttribute("fill", rgb);
						rgb = Math.floor(red * black + 0.5).toString() + "," + Math.floor(green * black + 0.5).toString() + "," + Math.floor(blue * black + 0.5).toString();
						rgbInput.value = rgb; swatch.style.backgroundColor = "rgb(" + rgb + ")";
						barPick.setAttribute("fill","rgb(" + rgb + ")");
						if(j == 0 || j == 2){ alphaPick.setAttribute("stroke","rgb(" + rgb + ")"); }
						if(j == 3){ alphaPick.setAttribute("fill","rgba(" + rgb + "," + styles[3][element][6].toString() + ")"); }
						if(j == 4){ blurPick.setAttribute("stroke","rgb(" + rgb + ")"); }
					}

					document.getElementById("colorWheel").addEventListener("mousemove", dragWheel);
					document.addEventListener("mouseup", stopWheel);

					function dragWheel(e) { var e = window.event || e; x = e.clientX; y = e.clientY + window.pageYOffset; colorWheel(x, y); }

					function stopWheel() {
					    document.getElementById("colorWheel").removeEventListener("mousemove", dragWheel);
					    styles[j][element][0] = red; styles[j][element][1] = green; styles[j][element][2] = blue;
					    styles[j][element][4] = outX; styles[j][element][5] = outY;
					    styles[j][element][8] = Math.floor(red * black + 0.5);
					    styles[j][element][9] = Math.floor(green * black + 0.5);
					    styles[j][element][10] = Math.floor(blue * black + 0.5);
					    delay(zoomPan, 0);
					}
				}

				if(e.target.id == "colorBar"){
				    ratio = 159 / ratio;
					++zoomPan;
					red = styles[j][element][0]; green = styles[j][element][1]; blue = styles[j][element][2];
					colorBar(y);

					function colorBar(y){
						y = ratio * (y - svgTop);
						barPick.setAttribute("y", String(y - 1));
						black = Math.min(1, Math.max(0, (130.5 - y) / 129));
						rgb = Math.floor(red * black + 0.5).toString() + "," + Math.floor(green * black + 0.5).toString() + "," + Math.floor(blue * black + 0.5).toString();
						rgbInput.value = rgb; swatch.style.backgroundColor = "rgb(" + rgb + ")";
						barPick.setAttribute("fill","rgb(" + rgb + ")");
						if(j == 0 || j == 2){ alphaPick.setAttribute("stroke","rgb(" + rgb + ")"); }
						if(j == 3){ alphaPick.setAttribute("fill","rgba(" + rgb + "," + styles[3][element][6].toString() + ")"); }
						if(j == 4){ blurPick.setAttribute("stroke","rgb(" + rgb + ")"); }
					}

					document.getElementById("colorBar").addEventListener("mousemove", dragBar);
					document.addEventListener("mouseup", stopBar);

					function dragBar(e) { var e = window.event || e; y = e.clientY + window.pageYOffset; colorBar(y); }

					function stopBar() {
					    document.getElementById("colorBar").removeEventListener("mousemove", dragBar);
					    styles[j][element][3] = black;
					    styles[j][element][8] = Math.floor(styles[j][element][0] * black + 0.5);
					    styles[j][element][9] = Math.floor(styles[j][element][1] * black + 0.5);
					    styles[j][element][10] = Math.floor(styles[j][element][2] * black + 0.5);
					    delay(zoomPan, 1);
					}
				}

				if(e.target.id == "alphaBar"){
				    ++zoomPan;
				    ratio = 162 / ratio;
					var color = rgbInput.value;
					if(j == 4){ stdDev = document.getElementById("stdDevPick");}
					alpha(x);

					function alpha(x){
						x = Math.max(6,Math.min(153,ratio * (x - svgLeft)));
						alphaPick.setAttribute("cx",x); blurPick.setAttribute("cx",x);
						outX = (x - 6) / 147;
						if(j == 0 || j == 2){ alphaPick.setAttribute("stroke-width",String(0.1 + 2 * outX)); }
						if(j == 3){ alphaPick.setAttribute("fill","rgba(" + color + "," + outX.toString() + ")"); }
						if(j == 4){
							blurPick.setAttribute("stroke-width",String(0.2 + 5 * outX));
							stdDev.setAttribute("stdDeviation",String(0.5 + 0.9 * outX));
						}
					}

					document.getElementById("alphaBar").addEventListener("mousemove", dragAlpha);
					document.addEventListener("mouseup", stopAlpha);

					function dragAlpha(e){ var e = window.event || e; x = e.clientX; alpha(x); }

					function stopAlpha() {
					    document.getElementById("alphaBar").removeEventListener("mousemove", dragAlpha);
					    styles[j][element][6] = outX; delay(zoomPan, 2);
					}
				}

				function delay(count, i){
					if(i == 0){ document.removeEventListener("mouseup", stopWheel); }
					if(i == 1){ document.removeEventListener("mouseup", stopBar); }
					if(i == 2){ document.removeEventListener("mouseup", stopAlpha); }
					setTimeout(function () {
					    if (count == zoomPan) {
					        if (styles[j][element][7] % 2 == 1) {
					            document.body.classList.add("wait"); waitWrap.classList.add("disable");
					            setTimeout(function () {
					                styling(j, element);
					                setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
					            }, 10);
					        }
					    }
					}, 500);
				}
			}

			function styling(i,j) {

				if(styles[i][j][7] % 2 == 0){ var color = "none"; }
				else{
				    if (i == 3) { var color = "rgba(" + styles[3][j][8].toString() + "," + styles[3][j][9].toString() + "," + styles[3][j][10].toString() + "," + styles[3][j][6].toString() + ")"; }
					else{ var color = "rgb(" + styles[i][j][8].toString() + "," + styles[i][j][9].toString() + "," + styles[i][j][10].toString() + ")"; }
				}

				if(i == 0){
					if(viewer.firstChild){
						viewer.childNodes[0].setAttribute("stroke", color);
						viewer.childNodes[0].setAttribute("stroke-width", String((0.0002 + 0.004 * styles[0][0][6]) * canvasWidth));
					}
					else{
					    if(styles[0][0][7] % 2 == 1){ canvas.style.border = String(1 + styles[0][0][6] * 15) + "em solid " + color; }
						else{ canvas.style.border = "none"; }
					}
				}

				if(i == 1){ background.setAttribute("fill",color); }

				if(i == 2){
				    var thick = String(0.003 * canvasWidth * (0.1 + 3 * styles[2][j][6]));
				    if (j < total) {
				        for (var r = 0; r <= maxR; r++) {
				            var curvLayer = document.getElementById(r.toString()), layer = curvLayer.childNodes[j];
				            for (var k = 0; k < layer.childNodes.length; k++) {
				            	var element = layer.childNodes[k];
				               if (element.tagName != "text" && element.hasAttribute("filter") == false) {
				                    element.setAttribute("stroke", color);
				                    element.setAttribute("stroke-width", thick);
				                }
				            }
				        }
				    }
				    if (j == total) {
				        for (var k = 0; k < selectCount; k++) {
				            if (selectArray[k][5] == 1) {
				                var child = selectCircles.childNodes[2 * k + 1];
				                child.setAttribute("stroke", color); child.setAttribute("stroke-width", thick);
				                selectArray[k][6] = styles[2][total][6];
				            }
				        }
				    }
				}

				if (i == 3) {
				    if (j < total) {
				        for (var r = 0; r <= maxR; r++) {
				            var curvLayer = document.getElementById(r.toString()), layer = curvLayer.childNodes[j];
				            for (var k = 0; k < layer.childNodes.length; k++) { 
				            	var element = layer.childNodes[k];
				               if (element.tagName != "text"){
				            		element.setAttribute("fill", color);
				            	}
				            }
				        }
				    }
				    if (j == total) {
				        for (var k = 0; k < selectCount; k++) {
				            if (selectArray[k][5] == 1) {
				                var child = selectCircles.childNodes[2 * k + 1];
				                child.setAttribute("fill", color);
				                selectArray[k][6] = styles[3][total][6];
				            }
				        }
				    }
				}

				if(i == 4){
				    if (color != "none") {
				        var alpha = styles[4][j][6];
					    var thick = 0.005 * canvasWidth * (0.05 + 3 * alpha);
					    if (j < total) {
					        document.getElementById("stdDev" + j.toString()).setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * alpha)));
					        for (var r = 0; r <= maxR; r++) {
					            var curvLayer = document.getElementById(r.toString());
					            var layer = curvLayer.childNodes[j];
					            for (var k = 0; k < layer.childNodes.length; k += 2) {
					                var child = layer.childNodes[k];
					                if (child.hasAttribute("filter")) { child.setAttribute("stroke", color); child.setAttribute("stroke-width", thick); }
					                else {
					                    if (child.hasAttribute("data-value")) {
					                        var circle = document.createElementNS(NS, "rect");
					                        circle.setAttribute("fill", color); circle.setAttribute("stroke", "none");
					                        if (child.getAttribute("data-value") == "x") {
					                            circle.setAttribute("height", thick);
					                            circle.setAttribute("width", String(3 * canvasWidth));
					                            circle.setAttribute("x", child.getAttribute("x1"));
					                            circle.setAttribute("y", String(parseInt(child.getAttribute("y1")) - thick / 2));
					                        }
					                        else {
					                            circle.setAttribute("width", thick);
					                            circle.setAttribute("height", String(3 * canvasWidth));
					                            circle.setAttribute("y", child.getAttribute("y1"));
					                            circle.setAttribute("x", String(parseInt(child.getAttribute("x1")) - thick / 2));
					                        }
					                    }
					                    else {
					                        var circle = child.cloneNode();
					                        circle.setAttribute("stroke", color);
					                        circle.setAttribute("stroke-width", thick);
					                    }
					                    circle.setAttribute("filter", "url(#blurFilter" + j.toString() + ")");
					                    layer.insertBefore(circle, child);
					                }
					            }
					        }
					    }
					    if (j == total) {
					        for (var k = 0; k < selectCount; k++) {
					            if (selectArray[k][5] == 1) {
					                child = selectCircles.childNodes[2 * k];
					                document.getElementById("selectStdDev" + k.toString()).setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * alpha)));
					                child.style.visibility = "visible";
					                if (child.hasAttribute("width")) {
					                    child.setAttribute("fill", color);
					                    var width = parseFloat(child.getAttribute("width"));
					                    var height = parseFloat(child.getAttribute("height"));
					                    if (width < height) { child.setAttribute("width", thick); }
					                    else { child.setAttribute("height", thick); }
					                }
					                else { child.setAttribute("stroke", color); child.setAttribute("stroke-width", thick); }
					                selectArray[k][7] = styles[4][total][6];
					            }
					        }
					    }
					}
					else {
					    if (j < total) {
					        var check = 0;
					        for (var r = 0; r <= maxR; r++) {
					            var curvLayer = document.getElementById(r.toString()), layer = curvLayer.childNodes[j];
					            if (layer.childNodes.length > 0) {
					                if (layer.childNodes[0].hasAttribute("filter")) { check = 1; }
					                break;
					            }
					        }
					        if (check == 1) {
					            for (var r = 0; r <= maxR; r++) {
					                var curvLayer = document.getElementById(r.toString()), layer = curvLayer.childNodes[j], k = 0;
					                while (k < layer.childNodes.length) { layer.removeChild(layer.childNodes[k]); k++; }
					            }
					        }
					    }
					    for (var k = 0; k < selectCount; k++) {
					        if (selectArray[k][5] == 1) { selectCircles.childNodes[2 * k].style.visibility = "hidden"; }
					    }
					}
				}
			}

			function getStyleArray(red, green, blue) {

				let black = Math.max(red, green, blue) / 255;
				let x = 68, y = 66, rad = 0;
				if(black != 0){
					red = Math.min(255, Math.floor(red / black + 0.5));
					green = Math.min(255, Math.floor(green / black + 0.5));
					blue = Math.min(255, Math.floor(blue / black + 0.5));
					rad = Math.max(0, 1 - Math.min(red, green, blue) / 255);
				}
				else { red = 255; green = 255; blue = 255; }
				let array = [red, green, blue, black];
				if(rad != 0){
					red = Math.max(0, Math.floor((red - 255) / rad + 255.5));
					green = Math.max(0, Math.floor((green - 255) / rad + 255.5));
					blue = Math.max(0, Math.floor((blue - 255) / rad + 255.5));
					let theta = Math.PI * (blue / 765 - 1);
					if(green == 0 && blue == 255){
						theta = Math.PI * ((2 - red / 255) / 3 - 1);
						if(red == 0){ theta = -1 * Math.PI / 3; }
						if(red == 255){ theta = -2 * Math.PI / 3; }
					}
					if(red == 0 && blue == 255){
						theta = Math.PI * ((2 + green / 255) / 3 - 1);
						if(green == 0){ theta = -1 * Math.PI / 3; }
						if(green == 255){ theta = 0; }
					}
					if(red == 0 && green == 255){
						theta = Math.PI * ((4 - blue / 255) / 3 - 1);
						if(blue == 0){ theta = Math.PI / 3; }
						if(blue == 255){ theta = 0; }
					}
					if(blue == 0 && green == 255){
						theta = Math.PI * ((4 + red / 255) / 3 - 1);
						if(red == 0){ theta = Math.PI / 3; }
						if(red == 255){ theta = 2 * Math.PI / 3; }
					}
					if(blue == 0 && red == 255){
						theta = Math.PI * ((6 - green / 255) / 3 - 1);
						if(green == 0){ theta = Math.PI; }
						if(green == 255){ theta = 2 * Math.PI / 3; }
					}
					x += 64 * rad * Math.cos(theta); y = 66 - 64 * rad * Math.sin(theta);
				}
				array.push(x); array.push(y);
				return array;
			}

			function reset(){
			    if (canvas.getAttribute("viewBox") != String((maxWidth - initWidth) / 2) + " " + String((maxWidth - initWidth) / 2) + " " + initWidth.toString() + " " + initWidth.toString()) {
			        document.body.classList.add("wait"); waitWrap.classList.add("disable");
			        setTimeout(function () {
			            canvasWidth = initWidth; canvasLeft = canvasTop = (maxWidth - initWidth) / 2; delta = canvasWidth / containWidth;
			            canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
			            for (var i = 0; i < total; i++) {
			                document.getElementById("stdDev" + i.toString()).setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * styles[4][i][6])));
			            }
			            for (var j = 0; j < infoCount; j++) {
			                document.getElementById("selectStdDev" + j.toString()).setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * infoArray[j][7])));
			                var i = infoArray[j][3], newBlur = infoCircles.childNodes[2 * j];
			                var newStroke = infoCircles.childNodes[2 * j + 1], thick = 0.005 * canvasWidth * (0.05 + 3 * infoArray[j][7]);
			                newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * infoArray[j][6])));
			                if (newBlur.hasAttribute("width")) {
			                    if (parseFloat(newBlur.getAttribute("height")) < parseFloat(newBlur.getAttribute("width"))) {
			                        newBlur.setAttribute("height", thick.toString());
			                        newBlur.setAttribute("y", String(parseFloat(newStroke.getAttribute("y1")) - thick / 2));
			                    }
			                    else {
			                        newBlur.setAttribute("width", thick.toString());
			                        newBlur.setAttribute("x", String(parseFloat(newStroke.getAttribute("x1")) - thick / 2));
			                    }
			                }
			                else { newBlur.setAttribute("stroke-width", thick.toString()); }
			                var label = document.getElementById("labels" + j.toString()).parentNode;
			                var transform = label.getAttribute("transform"); transform = transform.split(" ");
			                label.setAttribute("transform", transform[0] + " scale(" + String(canvasWidth / initWidth) + ")");
			            }
			            var i = coords[3]; if (i >= total) { i = 0; }
			            stdDevHL.setAttribute("stdDeviation", document.getElementById("stdDev" + i.toString()).getAttribute("stdDeviation"));
			            for (var j = 0; j < blur.childNodes.length; j++) {
			                var element = blur.childNodes[j];
			                if (element.nodeType == 1) { var newBlur = element; break; }
			            }
			            for (var j = 0; j < stroke.childNodes.length; j++) {
			                var element = stroke.childNodes[j];
			                if (element.nodeType == 1) { var newStroke = element; break; }
			            }
			            var thick = 0.005 * canvasWidth * (0.05 + 3 * styles[4][i][6]);
			            newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][i][6])));
			            if (newBlur.hasAttribute("width")) {
			                if (parseFloat(newBlur.getAttribute("height")) < parseFloat(newBlur.getAttribute("width"))) {
			                    newBlur.setAttribute("height", thick.toString());
			                    newBlur.setAttribute("y", String(parseFloat(newStroke.getAttribute("y1")) - thick / 2));
			                }
			                else {
			                    newBlur.setAttribute("width", thick.toString());
			                    newBlur.setAttribute("x", String(parseFloat(newStroke.getAttribute("x1")) - thick / 2));
			                }
			            }
			            else { newBlur.setAttribute("stroke-width", thick.toString()); }
			            if (coverings == 0) { for (var i = 0; i < total; i++) { render(i); } }
			            setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
			        }, 10);
				}
			}

			function setCurv(e) {

			    ++zoomPan;
				var e = window.event || e;
				var curv = document.getElementById("curv");
				var maxCurv = Math.floor(1000 * (26.5 - 2 * sqrt / two) / canvasWidth);

				if (e.type == "mousewheel" || e.type == "DOMMouseScroll") {
				    curv.value = String(Math.min(maxCurv, Math.max(0, parseInt(curv.value) + Math.max(-1, Math.min(1, (e.wheelDelta || -e.detail))))));
				    delay(zoomPan);
				}

				if (e.type == "click") {
				    var i = 0;
				    if (e.target.id == "curvDown") { i = -1; }
				    if (e.target.id == "curvUp") { i = 1; }
				    if (i != 0) {
				        curv.value = String(Math.min(maxCurv, Math.max(0, parseInt(curv.value) + i)));
				        delay(zoomPan);
				    }
				}

				function delay(count){
					setTimeout(function(){
					    if (count == zoomPan) {
					        document.body.classList.add("wait"); waitWrap.classList.add("disable");
					        setTimeout(function () {
							    R = parseInt(curv.value);
							    curvSet = canvasWidth;
							    for(var i = 0; i < total; i++){ render(i); }
							    setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
					        }, 10);
						}
					}, 600);
				}
			}

			function download() {

				var fileType = parseInt(document.getElementById("header5").getAttribute("data-value"));
				var fileName = document.getElementById("fileName").value, check = 0, link = document.createElement("a");
				if(fileName.length < 1){ check = 1; }
				else{
					var chars = ["NUL", "\\", "/", ":", "*", "\"", "<", ">", "|"];
					for(var i = 0; i < chars.length; i++){
						if (fileName.indexOf(chars[i]) > -1){ check = 1; break; }
					}
				}
				if(check == 1){
					if(fileType > 3){ fileName = d.toString() + "_data"; }
					else{ fileName = d.toString() + "_arrangement";}
				}

				if (fileType == 0) {

				    var pdf = new PDFDocument({ size: [612, 612], margin: { top: 0, left: 0, right: 0, bottom: 0 } });
				    pdf.font('Times-Roman')
				    var stream = pdf.pipe(blobStream());
				    var ratio = 610 / canvasWidth; check = 0, resolution = 2000;
				    
				    //weird for job talk
				    var scale2 = scale;

                    //background
				    if (styles[1][0][7] % 2 == 1) { pdf.rect(-1, -1, 614, 614).fillColor([styles[1][0][8], styles[1][0][9], styles[1][0][10]]).fill(); }

				    //background blur circles
				    var copy = document.createElementNS(NS, "svg");
				    copy.setAttribute("width", resolution); copy.setAttribute("height", resolution);
				    copy.setAttribute("viewBox", canvasLeft + " " + canvasTop + " " + canvasWidth + " " + canvasWidth);
				    copy.setAttribute("xmlns", "http://www.w3.org/2000/svg");

				    if (coverings == 0) {
				        for (var i = 0; i < canvas.childNodes.length; i++) {
				            var id = canvas.childNodes[i].id; if (!id) { break; }
				            var element = canvas.childNodes[i].cloneNode(true);
				            if (id.indexOf("blurFilter") != -1) { copy.appendChild(element); }
				        }
                        for (var r = 0; r < arrangement.childNodes.length; r++) {
				            var curvLayer = arrangement.childNodes[r];
				            for (var i = 0; i < curvLayer.childNodes.length; i++) {
				                if (styles[4][i][7] % 2 == 1 && visible[i] == 1) {
				                    check = 1;
				                    var layer = curvLayer.childNodes[i];
				                    for (var j = 0; j < layer.childNodes.length; j++) {
				                        var element = layer.childNodes[j].cloneNode(true);
				                        if (element.hasAttribute("filter")) { copy.appendChild(element); }
				                    }
				                }
				            }
				        }
				    }
				    
				    if (check == 1) {
				        var output = document.createElement("canvas"), context = output.getContext("2d");
				        var blank = document.createElement("canvas");
				        blank.width = blank.height = output.width = output.height = resolution;
				        var svgString = new XMLSerializer().serializeToString(copy);
				        var DOMURL = self.URL || self.webkitURL || self, img = new Image();
				        var svg = new Blob([svgString], { type: "image/svg+xml;charset=utf-8" }), url = DOMURL.createObjectURL(svg);
				        img.src = url;
				        img.onload = function () { context.drawImage(img, 0, 0, resolution, resolution); }

				        var test = setInterval(function () {
				            if (output.toDataURL() != blank.toDataURL()) { addImage(); clearInterval(test); }
				        }, 100);

				        function addImage() {
				            var imgData = output.toDataURL("image/png", 1.0);
				            pdf.image(imgData, 1, 1, { width: 610, height: 610 });
				            continuePDF();
				        }
				    }
				    else { continuePDF(); }

				    function continuePDF() {
							
				        
				        //arrangement circles
				        if (coverings == 0) {
				            for (var r = 0; r < arrangement.childNodes.length; r++) {
				                var curvLayer = arrangement.childNodes[r];
				                for (var i = 0; i < curvLayer.childNodes.length; i++) {
				                    if (visible[i] == 1) {
				                        var layer = curvLayer.childNodes[i];
				                        for (var j = 0; j < layer.childNodes.length; j++) {
				                            var element = layer.childNodes[j];
				                            if (element.tagName == "circle" && element.hasAttribute("filter") == false && element.style.visibility != "hidden") {
				                                var centX = 1 + ratio * (parseFloat(element.getAttribute("cx")) - canvasLeft);
				                                var centY = 1 + ratio * (parseFloat(element.getAttribute("cy")) - canvasTop);
				                                var rad = ratio * parseFloat(element.getAttribute("r"));
				                                if (centX + rad > 1 && centX - rad < 611 && centY + rad > 1 && centY - rad < 611) {
				                                    var stroke = element.getAttribute("stroke");
				                                    if (stroke != "none") {
				                                    	 var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                                        var fill = element.getAttribute("fill");
				                                        if (fill != "none") {
				                                            fill = fill.substring(fill.indexOf("(") + 1);
				                                            fill = fill.slice(0, -1); fill = fill.split(",");
				                                            pdf.circle(centX, centY, rad).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                                        }
				                                        else {
				                                            pdf.circle(centX, centY, rad).lineWidth(thick).strokeColor(stroke).stroke();
				                                        }
				                                    }
				                                    else {
				                                        var fill = element.getAttribute("fill");
				                                        if (fill != "none") {
				                                            fill = fill.substring(fill.indexOf("(") + 1);
				                                            fill = fill.slice(0, -1); fill = fill.split(",");
				                                            pdf.circle(centX, centY, rad).fillColor([fill[0], fill[1], fill[2]], fill[3]).fill();
				                                        }
				                                    }
				                                }
				                            }
				                            if (element.tagName == "line" && element.hasAttribute("filter") == false) {
				                                var x1 = 1 + ratio * (parseFloat(element.getAttribute("x1")) - canvasLeft);
				                                var x2 = 1 + ratio * (parseFloat(element.getAttribute("x2")) - canvasLeft);
				                                var y1 = 1 + ratio * (parseFloat(element.getAttribute("y1")) - canvasTop);
				                                var y2 = 1 + ratio * (parseFloat(element.getAttribute("y2")) - canvasTop);
				                                if ((x1 > 0 || x2 > 0) && (x1 < 612 || x2 < 612) && (y1 > 0 || y2 > 0) && (y1 < 612 || y2 < 612)) {
				                                    var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                                    var stroke = element.getAttribute("stroke");
				                                    if (stroke != "none") {
				                                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                                        pdf.lineCap("round").moveTo(x1, y1).lineTo(x2, y2).lineWidth(thick).strokeColor(stroke).stroke();
				                                    }
				                                }
				                            }
				                            if (element.tagName == "text") {
				                            	var text = element.innerHTML;
				                            	var translateX = 1 + ratio * (parseFloat(element.getAttribute("x")) - canvasLeft);     
														var translateY = 1 + ratio * (parseFloat(element.getAttribute("y")) - canvasTop);
				                        		var size = ratio * element.getAttribute("font-size");
				                        		var fill = element.getAttribute("fill");
				                        		fill = fill.substring(fill.indexOf("(") + 1);
				                        		fill = fill.slice(0, -1); fill = fill.split(",");
				                        		pdf.fontSize(size).fillColor("black");
				                        		var w = pdf.widthOfString(text);
				                        		var x = translateX - 0.5 * w, y = translateY - 0.32 * pdf.heightOfString(text, { width: w });
				                        		pdf.text(text, x, y, { width: pdf.page.width, height: pdf.page.height });
				                        	}
				                        }
				                    }
				                }
				            }
				            
				            
			                	
				        }
				        else {
				            var cover = document.getElementById("cover" + detChoice.toString());
				            for (var i = 0; i < cover.childNodes.length; i++) {
				                var element = cover.childNodes[i];
				                if (element.tagName == "circle" && element.style.visibility != "hidden") {
				                    var centX = 1 + ratio * (parseFloat(element.getAttribute("cx")) - canvasLeft);
				                    var centY = 1 + ratio * (parseFloat(element.getAttribute("cy")) - canvasTop);
				                    var rad = ratio * parseFloat(element.getAttribute("r"));
				                    if (centX + rad > 1 && centX - rad < 611 && centY + rad > 1 && centY - rad < 611) {
				                        if (element.hasAttribute("stroke-width")) { var thick = ratio * parseFloat(element.getAttribute("stroke-width")); }
				                        var stroke = element.getAttribute("stroke");
				                        if (stroke != "none") {
				                            stroke = stroke.substring(stroke.indexOf("(") + 1);
				                            stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                            var fill = element.getAttribute("fill");
				                            if (fill != "none") {
				                                fill = fill.substring(fill.indexOf("(") + 1);
				                                fill = fill.slice(0, -1); fill = fill.split(",");
				                                demo.innerHTML = fill;
				                                pdf.circle(centX, centY, rad).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                            }
				                            else {
				                                pdf.circle(centX, centY, rad).lineWidth(thick).strokeColor(stroke).stroke();
				                            }
				                        }
				                        else {
				                            var fill = element.getAttribute("fill");
				                            if (fill != "none") {
				                                fill = fill.substring(fill.indexOf("(") + 1);
				                                fill = fill.slice(0, -1); fill = fill.split(",");
				                                pdf.circle(centX, centY, rad).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).fill();
				                            }
				                        }
				                    }
				                }
				                if (element.tagName == "rect") {
				                    var x = 1 + ratio * (parseFloat(element.getAttribute("x")) - canvasLeft);
				                    var y = 1 + ratio * (parseFloat(element.getAttribute("y")) - canvasTop);
				                    var width = ratio * parseFloat(element.getAttribute("width"));
				                    if (element.hasAttribute("stroke-width")) { var thick = ratio * parseFloat(element.getAttribute("stroke-width")); }
				                    var stroke = element.getAttribute("stroke");
				                    if (stroke != "none") {
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.rect(x, y, width, width).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                        }
				                        else {
				                            pdf.rect(x, y, width, width).lineWidth(thick).strokeColor(stroke).stroke();
				                        }
				                    }
				                    else {
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.rect(x, y, width, width).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).fill();
				                        }
				                    }
				                }
				                if (element.tagName == "path") {
				                    var dString = element.getAttribute("d");
				                    dString = dString.split(" ");
				                    var startX = dString[1].split(","), startY = 1 + ratio * (parseFloat(startX[1]) - canvasTop);
				                    startX = 1 + ratio * (parseFloat(startX[0]) - canvasLeft);
				                    var rad = dString[3].split(",");
				                    var endX = 1 + ratio * (parseFloat(rad[5]) - canvasLeft);
				                    var endY = 1 + ratio * (parseFloat(rad[6]) - canvasTop);
				                    var aa = rad[2], bb = rad[3], cc = rad[4];
				                    rad = ratio * parseFloat(rad[0]);
				                    dString = "M " + startX.toString() + "," + startY.toString() + " A " + rad.toString() + "," + rad.toString() + "," + aa.toString() + "," + bb.toString() + "," + cc.toString() + "," + endX.toString() + "," + endY.toString();
				                    if (element.hasAttribute("stroke-width")) { var thick = ratio * parseFloat(element.getAttribute("stroke-width")); }
				                    var stroke = element.getAttribute("stroke");
				                    if (stroke != "none") {
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.path(dString).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                        }
				                        else {
				                            pdf.path(dString).lineWidth(thick).strokeColor(stroke).stroke();
				                        }
				                    }
				                    else {
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.path(dString).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).fill();
				                        }
				                    }
				                }
				                if (element.tagName == "line") {
				                    var x1 = 1 + ratio * (parseFloat(element.getAttribute("x1")) - canvasLeft);
				                    var y1 = 1 + ratio * (parseFloat(element.getAttribute("y1")) - canvasTop);
				                    var x2 = 1 + ratio * (parseFloat(element.getAttribute("x2")) - canvasLeft);
				                    var y2 = 1 + ratio * (parseFloat(element.getAttribute("y2")) - canvasTop);
				                    if (element.hasAttribute("stroke-width")) { var thick = ratio * parseFloat(element.getAttribute("stroke-width")); }
				                    var stroke = element.getAttribute("stroke");
				                    if (stroke != "none") {
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        pdf.lineCap("round").lineWidth(thick).strokeColor(stroke).moveTo(x1, y1).lineTo(x2, y2).stroke();
				                    }
				                }
				            }
				        }
				        
				        pdf.fillOpacity(1);
							
				        //selected blur circles
				        if (selectCount < 0) {
						
				            var copy = document.createElementNS(NS, "svg");
				            copy.setAttribute("width", resolution); copy.setAttribute("height", resolution);
				            copy.setAttribute("viewBox", canvasLeft + " " + canvasTop + " " + canvasWidth + " " + canvasWidth);
				            copy.setAttribute("xmlns", "http://www.w3.org/2000/svg");
				            for (var i = 0; i < canvas.childNodes.length; i++) {
				                var id = canvas.childNodes[i].id; if (!id) { break; }
				                var element = canvas.childNodes[i].cloneNode(true);
				                if (id.indexOf("infoFilter") != -1) { copy.appendChild(element); }
				                if (id.indexOf("selectFilter") != -1) { copy.appendChild(element); }
				            }
				            for (var i = 0; i < infoCount; i++) {
				                var element = infoCircles.childNodes[2 * i].cloneNode(true);
				                copy.appendChild(element);
				            }
				            for (var i = 0; i < selectCount; i++) {
				                var element = selectCircles.childNodes[2 * i].cloneNode(true);
				                copy.appendChild(element);
				            }
				            var output = document.createElement("canvas"), context = output.getContext("2d");
				            var blank = document.createElement("canvas");
				            blank.width = blank.height = output.width = output.height = resolution;
				            var svgString = new XMLSerializer().serializeToString(copy);
				            var DOMURL = self.URL || self.webkitURL || self, img = new Image();
				            var svg = new Blob([svgString], { type: "image/svg+xml;charset=utf-8" }), url = DOMURL.createObjectURL(svg);
				            img.src = url;
				            img.onload = function () { context.drawImage(img, 0, 0, resolution, resolution); }

				            var test = setInterval(function () {
				                if (output.toDataURL() != blank.toDataURL()) { addImage(); clearInterval(test); }
				            }, 100);

				            function addImage() {
				                var imgData = output.toDataURL("image/png", 1.0);
				                pdf.image(imgData, 1, 1, { width: 610, height: 610 });
				                completePDF();
				            }
				        }
				        else { completePDF(); }
				    }

				    function completePDF() {

                        //selected stroke circles
				        for (var i = 1000; i < infoCircles.childNodes.length; i++) {
				            var element = infoCircles.childNodes[i].cloneNode(true);
				            if (element.tagName == "circle" && element.hasAttribute("filter") == false) {
				                var centX = 1 + ratio * (parseFloat(element.getAttribute("cx")) - canvasLeft);
				                var centY = 1 + ratio * (parseFloat(element.getAttribute("cy")) - canvasTop);
				                var rad = ratio * parseFloat(element.getAttribute("r"));
				                if (centX + rad > 1 && centX - rad < 611 && centY + rad > 1 && centY - rad < 611) {
				                    var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                    var stroke = element.getAttribute("stroke");
				                    stroke = stroke.substring(stroke.indexOf("(") + 1);
				                    stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                    var fill = element.getAttribute("fill");
				                    if (fill != "none") {
				                        fill = fill.substring(fill.indexOf("(") + 1);
				                        fill = fill.slice(0, -1); fill = fill.split(",");
				                        pdf.circle(centX, centY, rad).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                    }
				                    else {
				                        pdf.circle(centX, centY, rad).lineWidth(thick).strokeColor(stroke).stroke();
				                    }
				                }
				            }
				            if (element.tagName == "line" && element.hasAttribute("filter") == false) {
				                var x1 = 1 + ratio * (parseFloat(element.getAttribute("x1")) - canvasLeft);
				                var x2 = 1 + ratio * (parseFloat(element.getAttribute("x2")) - canvasLeft);
				                var y1 = 1 + ratio * (parseFloat(element.getAttribute("y1")) - canvasTop);
				                var y2 = 1 + ratio * (parseFloat(element.getAttribute("y2")) - canvasTop);
				                if ((x1 > 0 || x2 > 0) && (x1 < 612 || x2 < 612) && (y1 > 0 || y2 > 0) && (y1 < 612 || y2 < 612)) {
				                    var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                    var stroke = element.getAttribute("stroke");
				                    stroke = stroke.substring(stroke.indexOf("(") + 1);
				                    stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                    pdf.lineCap("round").moveTo(x1, y1).lineTo(x2, y2).lineWidth(thick).strokeColor(stroke).stroke();
				                }
				            }
				        }
				        for (var i = 0; i < selectCircles.childNodes.length; i++) {

				            var element = selectCircles.childNodes[i].cloneNode(true);
				            if (element.tagName == "circle" && element.hasAttribute("filter") == false) {
				                var centX = 1 + ratio * (parseFloat(element.getAttribute("cx")) - canvasLeft);
				                var centY = 1 + ratio * (parseFloat(element.getAttribute("cy")) - canvasTop);
				                var rad = ratio * parseFloat(element.getAttribute("r"));
				                if (centX + rad > 1 && centX - rad < 611 && centY + rad > 1 && centY - rad < 611) {
				                    var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                    var stroke = element.getAttribute("stroke");
				                    if (stroke != "none") {
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.circle(centX, centY, rad).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                        }
				                        else {
				                            pdf.circle(centX, centY, rad).lineWidth(thick).strokeColor(stroke).stroke();
				                        }
				                    }
				                    else {
				                        var fill = element.getAttribute("fill");
				                        if (fill != "none") {
				                            fill = fill.substring(fill.indexOf("(") + 1);
				                            fill = fill.slice(0, -1); fill = fill.split(",");
				                            pdf.circle(centX, centY, rad).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).fill();
				                        }
				                    }
				                }
				            }
				            if (element.tagName == "line" && element.hasAttribute("filter") == false) {
				                var x1 = 1 + ratio * (parseFloat(element.getAttribute("x1")) - canvasLeft);
				                var x2 = 1 + ratio * (parseFloat(element.getAttribute("x2")) - canvasLeft);
				                var y1 = 1 + ratio * (parseFloat(element.getAttribute("y1")) - canvasTop);
				                var y2 = 1 + ratio * (parseFloat(element.getAttribute("y2")) - canvasTop);
				                if ((x1 > 0 || x2 > 0) && (x1 < 612 || x2 < 612) && (y1 > 0 || y2 > 0) && (y1 < 612 || y2 < 612)) {
				                    var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                    var stroke = element.getAttribute("stroke");
				                    if(stroke != "none"){
				                    	stroke = stroke.substring(stroke.indexOf("(") + 1);
				                    	stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                    	pdf.lineCap("round").moveTo(x1, y1).lineTo(x2, y2).lineWidth(thick).strokeColor(stroke).stroke();
				                    }
				                }
				            }

				        }

				        //labels
				        for (var i = 0; i < infoLabels.childNodes.length; i++) {
				            var group = infoLabels.childNodes[i];
				            if (group.tagName == "g") {
				                var transform = group.getAttribute("transform");
				                var translateX = 1 + ratio * (parseFloat(transform.substring(transform.indexOf("(") + 1, transform.indexOf(","))) - canvasLeft);
				                var translateY = 1 + ratio * (parseFloat(transform.substring(transform.indexOf(",") + 1, transform.indexOf(")"))) - canvasTop);
				                transform = transform.split(" ");
				                var scale = ratio * parseFloat(transform[1].substring(transform[1].indexOf("(") + 1, transform[1].indexOf(")")));
				                for (var j = 0; j < group.childNodes.length; j++) {
				                    var element = group.childNodes[j];
				                    if (element.tagName == "rect") {
				                        var width = scale * parseFloat(element.getAttribute("width"));
				                        var divide = 19 / width; width = 19;
				                        var x = translateX - 0.5 * width, y = translateY - 0.5 * width;
				                        var rad = divide * scale * parseFloat(element.getAttribute("rx"));
				                        var thick = scale * parseFloat(element.getAttribute("stroke-width"));
				                        var stroke = element.getAttribute("stroke");
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        var fill = element.getAttribute("fill");
				                        fill = fill.substring(fill.indexOf("(") + 1);
				                        fill = fill.slice(0, -1); fill = fill.split(",");
				                        pdf.roundedRect(x, y, width, width, rad).lineWidth(thick).fillColor(fill).strokeColor(stroke).fillAndStroke();
				                    }
				                    if (element.tagName == "text") {
				                        var text = element.innerHTML;
				                        var size = (divide * 0.85) * scale * element.getAttribute("font-size");
				                        var fill = element.getAttribute("fill");
				                        fill = fill.substring(fill.indexOf("(") + 1);
				                        fill = fill.slice(0, -1); fill = fill.split(",");
				                        pdf.fontSize(size).fillColor("black");
				                        var w = pdf.widthOfString(text);
				                        var x = translateX - 0.5 * w, y = translateY - 0.32 * pdf.heightOfString(text, { width: w });
				                        pdf.text(text, x, y, { width: pdf.page.width, height: pdf.page.height });
				                    }
				                    if(element.tagName == "circle"){
				            				var centX = ratio * parseFloat(element.getAttribute("cx")) + translateX;
				                        var centY = ratio * parseFloat(element.getAttribute("cy")) + translateY;
				                        var rad = scale * parseFloat(element.getAttribute("r"));
				                        if (centX + rad > 1 && centX - rad < 611 && centY + rad > 1 && centY - rad < 611) {
				                        	var stroke = element.getAttribute("stroke");
				                        	if (stroke != "none") {
				                        		var thick = ratio * parseFloat(element.getAttribute("stroke-width"));
				                        		stroke = stroke.substring(stroke.indexOf("(") + 1);
				                           	stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                           	var fill = element.getAttribute("fill");
				                           	if (fill != "none") {
				                           		fill = fill.substring(fill.indexOf("(") + 1);
				                              	fill = fill.slice(0, -1); fill = fill.split(",");
				                              	pdf.circle(centX, centY, rad).lineWidth(thick).fillColor([fill[0], fill[1], fill[2]]).fillOpacity(fill[3]).strokeColor(stroke).fillAndStroke();
				                           	}
				                           	else {
				                           		pdf.circle(centX, centY, rad).lineWidth(thick).strokeColor(stroke).stroke();
				                           	}
				                        	}
				                        	else {
				                        		var fill = element.getAttribute("fill");
				                           	if (fill != "none") {
				                           		fill = fill.substring(fill.indexOf("(") + 1);
				                              	fill = fill.slice(0, -1); fill = fill.split(",");
				                              	pdf.circle(centX, centY, rad).fillColor([fill[0], fill[1], fill[2]], fill[3]).fill();
				                           	}
				                        	}
				                      	}
				            		  }
				                }
				            }
				        }
				        for (var i = 0; i < selectLabels.childNodes.length; i++) {
				            var group = selectLabels.childNodes[i];
				            if (group.tagName = "g") {
				                var transform = group.getAttribute("transform");
				                var translateX = 1 + ratio * (parseFloat(transform.substring(transform.indexOf("(") + 1, transform.indexOf(","))) - canvasLeft);
				                var translateY = 1 + ratio * (parseFloat(transform.substring(transform.indexOf(",") + 1, transform.indexOf(")"))) - canvasTop);
				                transform = transform.split(" ");
				                var scale = ratio * parseFloat(transform[1].substring(transform[1].indexOf("(") + 1, transform[1].indexOf(")")));
				                for (var j = 0; j < group.childNodes.length; j++) {
				                    var element = group.childNodes[j];
				                    if (element.tagName == "rect") {
				                        var width = scale * parseFloat(element.getAttribute("width"));
				                        var divide = 40 / width; width = 40;
				                        var x = translateX - 0.5 * width, y = translateY - 0.5 * width;
				                        var rad = divide * scale * parseFloat(element.getAttribute("rx"));
				                        var thick = scale * parseFloat(element.getAttribute("stroke-width"));
				                        var stroke = element.getAttribute("stroke");
				                        stroke = stroke.substring(stroke.indexOf("(") + 1);
				                        stroke = stroke.slice(0, -1); stroke = stroke.split(",");
				                        var fill = element.getAttribute("fill");
				                        fill = fill.substring(fill.indexOf("(") + 1);
				                        fill = fill.slice(0, -1); fill = fill.split(",");
				                        pdf.roundedRect(x, y, width, width, rad).lineWidth(thick).fillColor(fill).strokeColor(stroke).fillAndStroke();
				                    }
				                    if (element.tagName == "text") {
				                        var text = element.innerHTML;
				                        var size = (divide * 0.85) * scale * element.getAttribute("font-size");
				                        var fill = element.getAttribute("fill");
				                        fill = fill.substring(fill.indexOf("(") + 1);
				                        fill = fill.slice(0, -1); fill = fill.split(",");
				                        pdf.fontSize(size).fillColor("black");
				                        var w = pdf.widthOfString(text);
				                        var x = translateX - 0.5 * w, y = translateY - 0.32 * pdf.heightOfString(text, { width: w });
				                        pdf.text(text, x, y, { width: pdf.page.width, height: pdf.page.height });
				                    }
				                }
				            }
				        }
						
							//job talk -23 and -1
				         if(1 == 1){
				         	var pdfRad = ratio * scale2 * 0.01;
				         	pdfRad = ratio * scale2 * 0.018;
                        var pdfX = ratio * (originX - scale2 * (56/72+0.01) - canvasLeft);
                        var pdfY = ratio * (originY - scale2 * (8*Math.sqrt(23)/72-0.02) - canvasTop);
								//job talk -1                        	
                        if(1 == 1){
                        	pdfX = 1 + ratio * (originX + scale2 * 0.335 - canvasLeft);
                        	pdfY = 1 + ratio * (originY - scale2 * 0.418 - canvasTop);
                        }
                        var thick = 0.15;
                        pdf.circle(pdfX, pdfY, pdfRad).lineWidth(thick).strokeColor([86,2,0]).fillColor([193,3,1]).fillOpacity(1).fillAndStroke();
                     }						
						
				        //window
				        pdf.path("M -10 -10 H 622 V 802 H -10 V -10 M 1 1 H 611 V 611 H 1 V 1").fill("white", "even-odd");

                        //download
				        pdf.end();
				        stream.on('finish', function () {
				            var pdfBlob = stream.toBlob('application/pdf');
				            var pdfUrl = URL.createObjectURL(pdfBlob);
				            link.setAttribute("href", pdfUrl);
				            link.setAttribute("download", fileName + ".pdf");
				            document.body.appendChild(link);
				            link.click();
				            document.body.removeChild(link);
				        });
				    }
				}

				if(fileType == 1){
					var svg = document.createElementNS(NS,"svg");
					var viewBox = canvas.getAttribute("viewBox"); svg.setAttribute("viewBox", viewBox);
					viewBox = viewBox.split(" ");
					var x1 = parseFloat(viewBox[0]), y1 = parseFloat(viewBox[1]), x2 = x1 + parseFloat(viewBox[2]), y2 = y1 + parseFloat(viewBox[3]);
					svg.setAttribute("width", canvas.clientWidth);
					svg.setAttribute("height", canvas.clientHeight);
					svg.setAttribute("xmlns", canvas.getAttribute("xmlns"));
					for(var i = 0; i < canvas.childNodes.length; i++){
						var node = canvas.childNodes[i].cloneNode(true);
						if(node.nodeType == 1){ svg.appendChild(node); }
					}
					var g = svg.childNodes[2];
					for(var i = 1; i < g.childNodes.length; i++){
						var r = g.childNodes[i], j = 0;
						while(j < r.childNodes.length){
							var layer = r.childNodes[j];
							if(layer.style.visibility == "hidden"){ r.removeChild(r.childNodes[j]); }
							else{
								var k = 0;
								while(k < layer.childNodes.length){
									var circle = layer.childNodes[k];
									var rad = circle.getAttribute("r"), centX = circle.getAttribute("cx"), centY = circle.getAttribute("cy");
									if((centX + rad <= x1 || centX - rad >= x2) || (centY + rad <= y1 || centY - rad >= y2)){ layer.removeChild(layer.childNodes[k]); }
									else{ k++; }
								}
								j++;
							}
						}
					}
					var svgData = svg.outerHTML;
                    var svgBlob = new Blob([svgData], { type: "image/svg+xml;charset=utf-8" });
                    var svgUrl = URL.createObjectURL(svgBlob);
                    link.setAttribute("href", svgUrl);
					link.setAttribute("download", fileName + ".svg");
					document.body.appendChild(link);
					link.click();
					document.body.removeChild(link);
				}

				if (fileType == 2 || fileType == 3) {
				    var resolution = 2500;
				    var output = document.createElement("canvas"), context = output.getContext("2d");
				    var blank = document.createElement("canvas");
				    blank.width = blank.height = output.width = output.height = resolution;
				    var svgString = new XMLSerializer().serializeToString(canvas);
				    var DOMURL = self.URL || self.webkitURL || self, img = new Image();
				    var svg = new Blob([svgString], { type: "image/svg+xml;charset=utf-8" }), url = DOMURL.createObjectURL(svg);
				    img.src = url;
				    img.onload = function () { context.drawImage(img, 0, 0, resolution, resolution); }
				    var test = setInterval(function () {
				        if (output.toDataURL() != blank.toDataURL()) { dload(); clearInterval(test); }
				    }, 100);

				    function dload() {
					    if (fileType == 3) {
					        var imgData = output.toDataURL("image/jpg", 1.0);
					        link.setAttribute("download", fileName + ".jpg");
					    }
					    else {
					        var imgData = output.toDataURL("image/png", 1.0);
					        link.setAttribute("download", fileName + ".png");
					    }
					    link.setAttribute("href", imgData);
					    document.body.appendChild(link);
					    link.click();
					    document.body.removeChild(link);
					}
				}

				if (fileType > 3) {
				    var viewBox = canvas.getAttribute("viewBox"); viewBox = viewBox.split(" ");
				    var x1 = (parseFloat(viewBox[0]) - originX) / scale, y1 = (originY - parseFloat(viewBox[1])) / scale, x2 = x1 + parseFloat(viewBox[2]) / scale, y2 = y1 - parseFloat(viewBox[3]) / scale;

				    var data = "data:text/", delim = ";";
				    if (fileType == 4) { data += "plain;charset=utf-8,"; link.setAttribute("download", fileName + ".txt"); }
				    else { data += "csv;charset=utf-8,"; delim = "\n"; link.setAttribute("download", fileName + ".csv"); }
				    check = 0; var header = ["rad", "cenX,cenY", "curv", "ccX,ccY", "Ideal"];
				    for (var i = 0; i < 5; ++i) { if (downLoad[i] == 1) { check = -1; data += header[i] + ","; } }
				    if (check == 0) { return; }
				    data = data.slice(0, -1); data += delim;
				    for (var i = 0; i < 3; i++) { if (document.getElementById("checkBox2," + i.toString()).innerHTML != "") { check = i; break; } }
				    if (check == -1) { return; }
				    for (var i = 0; i < total; i++) {
				        if (visible[i] == 1) {
				            data += "Element " + String(i % h + 1);
				            if (fileType == 4) { data += ":"; }
				            else { data += "\n"; }
				            var principal = prin[i];
				            var sqrtp = two * Math.sqrt(principal) / sqrt;
				            for (var r = 1; r < circArray[i].length; r++) {
				                var rad = sqrtp / (2 * r);
				                for (y = 0; y < circArray[i][r].length; y++) {
				                    var yy = circArray[i][r][y][0];
				                    var centY = yy / (2 * r * sqrt);
				                    if (check == 0 || (centY - rad < sqrt / two && centY + rad > 0)) {
				                        for (var k = 1; k < circArray[i][r][y].length; k++) {
				                            var x = circArray[i][r][y][k], centX = x / (2 * r);
				                            if (check != 2 || (centX + rad > (two - 1) * sqrt * centY && centX - rad < (two - 1) * sqrt * centY + 1)) {
				                                if ((centX + rad > x1 && centX - rad < x2) && (centY + rad > y2 && centY - rad < y1)) {
				                                    if (downLoad[0] == 1) { data += rad.toString() + ","; }
				                                    if (downLoad[1] == 1) { data += centX.toString() + "," + centY.toString() + ","; }
				                                    if (downLoad[2] == 1) { data += r.toString() + ","; }
				                                    if (downLoad[3] == 1) { data += x.toString() + "," + yy.toString() + ","; }
				                                    if (downLoad[4] == 1) { data += principal.toString() + ","; }
				                                    data = data.slice(0, -1);
				                                    data += delim;
				                                }
				                            }
				                        }
				                    }
				                }
				            }
				        }
				    }

				    var encodedUri = encodeURI(data);
				    link.setAttribute("href", encodedUri);
				    document.body.appendChild(link);
				    link.click();
				    document.body.removeChild(link);
				}
            }

			function check(i, j) {

                var checkBox = document.getElementById("checkBox" + i.toString() + "," + j.toString());
				if (checkBox.innerHTML == "") { checkBox.innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>"; }
				else{ checkBox.innerHTML = ""; }
				if(i == 1){
				    for (var k = 0; k < h; ++k) {
						var kk = reps[k][0][1], cayleyText = document.getElementById("cayleyText" + k.toString() + ".0");
						if (reps[kk][0][0] == -1) { kk -= 1; }
						if (kk == j && ((checkBox.innerHTML == "" && cayleyText.style.display != "none") || (checkBox.innerHTML != "" && cayleyText.style.display == "none"))) { collapse(k); }
				    }
					return;
				}

				if(i == 2){

				    if (viewer.firstChild) { viewer.removeChild(viewer.lastChild); }
					for (var k = 0; k < 3; k++) { if (k != j) { document.getElementById("checkBox2," + k.toString()).innerHTML = ""; } }
					var path = document.createElementNS(NS, "path");
					var points = "M -0.1 -0.1 H " + String(maxWidth + 0.1) + " V " + String(maxWidth + 0.1) + " H -0.1 Z";
					path.setAttribute("fill", "#FFF");
					if(checkBox.innerHTML != "") {
						if(styles[0][0][7] % 2 == 1){
							var color = "rgb(" + document.getElementById("rgb3").value + ")";
							if(j == 0){ canvas.style.border = String(0.01 + styles[0][0][6] * 0.15) + "em solid " + color; }
						}
						if (j != 0) {
							canvas.style.border = "none";
							if (j == 2) {
								points += " M " + originX.toString() + " " + originY.toString() + " h " + scale.toString() + " L ";
								points += String(scale * (two + 1) / 2 + originX) + " " + String(originY - scale * sqrt / two) + " h " + String(-1 * scale) + " Z";
							}
							else {
								points += " M -0.1 " + originY.toString() + " H " + String(maxWidth + 0.1);
								points += " v " + String(-1 * scale * sqrt / two) + " H -0.1 Z";
							}
							if(styles[0][0][7] % 2 == 1){
								path.setAttribute("stroke",color);
								path.setAttribute("stroke-width",String((0.0002 + 0.004 * styles[0][0][6]) * canvasWidth));
							}
							else{ path.setAttribute("stroke","none"); }
							path.setAttribute("d", points);
							path.setAttribute("fill-rule", "evenodd");
							viewer.appendChild(path);
						}
					}
					else {
					    if(styles[0][0][7] % 2 == 1){ canvas.style.border = String(styles[0][0][6] * 0.07) + "em solid " + color; }
					    path.setAttribute("stroke", "none"); path.setAttribute("d", points); viewer.appendChild(path);
					}
					return;
				}

				if(i == 3){
					var k = 0;
					if(j > 1){ k = parseInt(document.getElementById("header3").getAttribute("data-value")); }
					var alphaPick = document.getElementById("alphaPick"), blurPick = document.getElementById("blurPick");
					if (styles[j][k][7] % 2 != 0) {
					    styles[j][k][7] -= 1;
					    if (styles[j][k][7] > 1) { toggleColors(2, j); }
					    else {
					        if (document.getElementById("toggleAlpha").style.display == "block") {
					            if (styles[0][0][7] > 1) { if (j == 1) { alphaPick.setAttribute("fill", "white"); } }
					            else {
					                if (j == 2 && styles[2][k][7] < 2) { alphaPick.setAttribute("stroke", "none"); }
					                if (j == 3 && styles[3][k][7] < 2) { alphaPick.setAttribute("fill", "white"); }
					                if (j == 4 && styles[4][k][7] < 2) { blurPick.style.visibility = "hidden"; }
					            }
					        }
					    }

					}
					else { styles[j][k][7] += 1; toggleColors(1,j); }
					setTimeout(function(){ styling(j,k); }, 10);
					return;
				}

				if(i == 5){
					if (downLoad[j] == 0) { downLoad[j] = 1; }
					else{ downLoad[j] = 0; }
					return;
				}

				if (i == 8) {
				    if (detChoice == -1) {
				        if (selectArray[j][5] == 0) { selectArray[j][5] = 1; }
				        else { selectArray[j][5] = 0; }
				    }
				    else {
				        for (var k = 0; k < detList.length; k++) {
				            var cover = document.getElementById("cover" + k.toString());
				            for (var l = cover.childNodes.length - 1; l >= 0; l--) {
				                var element = cover.childNodes[l], gcd = parseFloat(element.getAttribute("data-value"));
				                gcd = Math.floor((gcd / scale) * (gcd / scale) * currentPrin + 0.5);
				                if (gcd == j) {
				                    if (checkBox.innerHTML == "") { element.style.visibility = "hidden"; }
				                    else { element.style.visibility = "visible"; }
				                }
				            }
				        }
				    }
				}
            }

			function closeList(e) {
			    var e = window.event || e, array = [[1], [3, 3], [5, 5], [7,7], [8,8]], target = e.target.id;
			    for (var i = 0; i > -1 * h; i--) { array[0].push(i); }
			    for (var i = 0; i < array.length; i++) {
			        for (var j = 1; j < array[i].length; j++) {
			            var k = array[i][0], l = array[i][j], toggle = document.getElementById("toggle" + k.toString() + "," + l.toString());
			            if (toggle != null && toggle.style.display == "block") {
			                if (target.indexOf("option") == -1 && target != "header" + l.toString()) { tog(k, l); }
			                document.removeEventListener("click", closeList, true); return;
			            }
			        }
			    }
			}

			function tog(i,j) {

				var toggle = document.getElementById("toggle" + i.toString() + "," + j.toString());
				var arrow = document.getElementById("arrow" + i.toString() + "," + j.toString());
				if (toggle.style.display == "block") {
                    toggle.style.display = "none"; arrow.src = "downarrow.jpg";
					if(i == 1){
						j *= -1;
						for (var k = 0; k < h; ++k) {
						    var kk = reps[k][0][1];
							if (reps[kk][0][0] == -1) { kk -= 1; }
							if (kk == j) {
							    document.getElementById("cayleyCell" + k.toString() + ".0").style.backgroundColor = "white";
							    if (k != 0) {
							        document.getElementById("cayleyCell0." + k.toString()).style.backgroundColor = "white";
							        document.getElementById("cayleyCell" + k.toString() + "." + k.toString()).style.backgroundColor = "white";
								}
							}
						}
					}
				}
				else {
					toggle.style.display = "block"; arrow.src = "uparrow.jpg";
					if (i != 0) { document.addEventListener("click", closeList, true); }
					if (i == 1) {
						j *= -1;
						for (var k = 0; k < h; ++k) {
							var kk = reps[k][0][1];
							if (reps[kk][0][0] == -1) { kk -= 1; }
							if (kk == j){
							    var m = 2, jj = k + total - h;
								for(var l = 2; l < 5; l++){ if(styles[l][jj][7] % 2 == 1){ m = l; break;} }
								var color = "rgb(" + styles[m][jj][8].toString() + "," + styles[m][jj][9].toString() + "," + styles[m][jj][10].toString() + ")";
								document.getElementById("cayleyCell" + k.toString() + ".0").style.backgroundColor = color;
								if(k != 0){
								    document.getElementById("cayleyCell0." + k.toString()).style.backgroundColor = color;
								    document.getElementById("cayleyCell" + k.toString() + "." + k.toString()).style.backgroundColor = "#c3cbd8";
								}
							}
						}
					}
				}
			}

            function keyPress(e) {
                ++zoomPan;
                var e = window.event || e, target = e.target.id;
                if (target.indexOf("rgb") != -1) {
                    var i = parseInt(target.slice(-1)), element = 0;
                    if (i > 1) { element = parseInt(document.getElementById("header3").getAttribute("data-value")); }
                    if (e.keyCode == 13) { registerRgb(); }
                    else { delayRgb(zoomPan); }

                    function delayRgb(count) { setTimeout(function () { if (count == zoomPan) { registerRgb(); } }, 800); }

                    function registerRgb() {
                        var rgb = document.getElementById(target).value, color = "rgb(" + rgb + ")";
                        rgb = rgb.split(",");
                        if (rgb.length != 3) { return; }
                        for (j = 2; j >= 0; j--) {
                            if (rgb[j] != parseInt(rgb[j])) { return; }
                            else { rgb[j] = parseInt(rgb[j]); if (0 > rgb[j] || 255 < rgb[j]) { return; } }
                        }
                        document.getElementById("swatch" + i.toString()).style.backgroundColor = color;
                        var styleArray = getStyleArray(rgb[0], rgb[1], rgb[2]);
                        for (var j = 0; j < 6; j++) { styles[i][element][j] = styleArray[j]; }
                        for (var j = 0; j < 3; j++) { styles[i][element][8 + j] = Math.floor(styleArray[j] * styleArray[3] + 0.5); }
                        setColors(i, element);
                        document.body.classList.add("wait"); waitWrap.classList.add("disable");
                        setTimeout(function () {
                            styling(i, element);
                            setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
                        }, 10);
                    }
                    return;
                }

                if (target == "curv") {
                    if (e.keyCode == 13) { registerCurv(); }
                    else { delayCurv(zoomPan); }

                    function delayCurv(count) { setTimeout(function () { if (count == zoomPan) { registerCurv(); } }, 800); }

                    function registerCurv() {
                        var maxCurv = Math.floor(250 * (26.5 - 2 * sqrt / two) / canvasWidth);
                        var curv = e.target.value;
                        if (curv == parseInt(curv)) {
                            curv = parseInt(curv);
                            if(curv < 0){ curv = 0; }
                            if (curv > maxCurv) { curv = maxCurv; }

                            if (curv != e.target.value) { e.target.value = curv.toString(); }
                            R = curv; curvSet = canvasWidth;
                            document.body.classList.add("wait");
                            setTimeout(function () {
                                waitWrap.classList.add("disable");
                                setTimeout(function () {
                                    for (var i = 0; i < total; i++) { render(i); }
                                    setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
                                }, 10);
                            }, 10);
                        }
                    }
                    return;
                }

                if (target == "disc") {
                    if (e.keyCode == 13) { document.getElementById("draw").click(); }
                    return;
                }
            }

            function toggleColors(i, j) {
				var element = parseInt(document.getElementById("header3").getAttribute("data-value")), k = 0;
				var toggleColors = document.getElementById("toggleColors"), toggleAlpha = document.getElementById("toggleAlpha");
				var swatch = document.getElementById("swatch" + j.toString());
				if(j > 1){ k = element; }
				if(i != 1 && styles[j][k][7] > 1){
				    toggleColors.style.display = "none";
				    toggleAlpha.style.display = "none";
					styles[j][k][7] -= 2;
					swatch.style.outlineOffset = "0";
					if (i == 2) { swatch.style.outlineStyle = "none"; }
					return;
				}
				if(i == 1 && styles[j][k][7] > 1) { return; }
				swatch.style.outlineStyle = "solid";
				swatch.style.outlineOffset = "1px";
				var array = [0,0,element,element,element];
				for(var l = 0; l < 5; l++){
					swatch = document.getElementById("swatch" + l.toString());
					if(styles[l][array[l]][7] > 1){
						styles[l][array[l]][7] -= 2;
						swatch.style.outlineOffset = "0";
						swatch.style.outlineStyle = "none";
					}
				}
				styles[j][k][7] += 2;
				if(toggleColors.style.display == "none"){ toggleColors.style.display = "block"; }
				if(j == 1){ toggleAlpha.style.display = "none"; }
				else { if (toggleAlpha.style.display == "none") { toggleAlpha.style.display = "block"; } }
				setColors(j,k);
			}

            function setColors(i, j) {
				var wheelPick = document.getElementById("wheelPick");
				wheelPick.setAttribute("cx",styles[i][j][4]); wheelPick.setAttribute("cy",styles[i][j][5]);
				var black = styles[i][j][3], alpha = styles[i][j][6];
				var color = "rgb(" + styles[i][j][0].toString() + "," + styles[i][j][1].toString() + "," + styles[i][j][2].toString() + ")";
				document.getElementById("stopBlack").style.stopColor = color;
				wheelPick.setAttribute("fill", color);
				color = "rgb(" + document.getElementById("rgb" + i.toString()).value + ")";
				var barPick = document.getElementById("barPick");
				barPick.setAttribute("fill",color);
				barPick.setAttribute("y",String(130.5 - 129 * black - 1));
				var alphaPick = document.getElementById("alphaPick"), blurPick = document.getElementById("blurPick");
				alphaPick.setAttribute("cx",String(6 + 147 * alpha));
				blurPick.setAttribute("cx",String(6 + 147 * alpha));
				if(i == 0){
					var bgColor = "white"
					if(styles[1][0][7] % 2 == 1){ bgColor = "rgb(" + document.getElementById("rgb1").value + ")"; }
					blurPick.style.visibility = "hidden";
					alphaPick.setAttribute("fill",bgColor);
					alphaPick.setAttribute("stroke",color);
					alphaPick.setAttribute("stroke-width",String(0.1 + 2 * alpha));
					return;
				}
				if(i == 1){ return; }
				var bgColor = "white", strokeColor = "none", strokeWidth = "0";
				if(styles[2][j][7] % 2 == 1 || i == 2){
				    strokeColor = "rgb(" + styles[2][j][8] + "," + styles[2][j][9] + "," + styles[2][j][10] + ")";
					strokeWidth = String(0.1 + 2 * styles[2][j][6]);
				}
				if (styles[3][j][7] % 2 == 1 || i == 3) { bgColor = "rgba(" + styles[3][j][8] + "," + styles[3][j][9] + "," + styles[3][j][10] + "," + styles[3][j][6].toString() + ")"; }
				if(styles[4][j][7] % 2 == 1 || i == 4){
					document.getElementById("stdDevPick").setAttribute("stdDeviation",String(0.5 + 0.9 * styles[4][j][6]));
					if(blurPick.style.visibility != "visible"){ blurPick.style.visibility = "visible"; }
					blurPick.setAttribute("stroke-width", String(0.2 + 5 * styles[4][j][6]));
					blurPick.setAttribute("stroke", "rgb(" + styles[4][j][8] + "," + styles[4][j][9] + "," + styles[4][j][10] + ")");
				}
				else{ blurPick.style.visibility = "hidden"; }
				alphaPick.setAttribute("fill",bgColor);
				alphaPick.setAttribute("stroke",strokeColor);
				alphaPick.setAttribute("stroke-width", strokeWidth);
			}

            function collapse(i) {

                var ii = reps[i][0][1];
                if (reps[ii][0][0] == -1) { ii -= 1; }
                if (document.getElementById("cayleyText" + i.toString() + ".0").style.display != "none") {

                    var check = 0;
                    if (coverings == 0) { visible[i + total - h] = 0; }
                    for (var j = 0; j < h; j++) {
                        var cayleyCell = document.getElementById("cayleyCell" + i.toString() + "." + j.toString());
                        if (j == 0 || i != 0) {
                            document.getElementById("cayleyText" + i.toString() + "." + j.toString()).style.display = "none";
                            cayleyCell.style.width = "0.5em"; cayleyCell.style.height = "0.5em";
                        }
                        var jj = reps[j][0][1];
                        if (reps[jj][0][0] == -1) { jj -= 1; }
                        if (jj == ii && document.getElementById("cayleyText" + j.toString() + ".0").style.display != "none") { check = 1; }
                        cayleyCell = document.getElementById("cayleyCell" + j.toString() + "." + i.toString());
                        if (i != 0) {
                            document.getElementById("cayleyText" + j.toString() + "." + i.toString()).style.display = "none";
                            cayleyCell.style.width = "0.5em"; cayleyCell.style.height = "0.5em";
                        }
                    }
                    if (check == 0) { document.getElementById("checkBox1," + ii.toString()).innerHTML = ""; }
                    if (coverings == 0) {
                        for (var r = 0; r <= maxR; r++) {
                            var curvLayer = document.getElementById(r.toString());
                            for (var j = 0; j < total / h; j++) { curvLayer.childNodes[h * j + i].style.visibility = "hidden" }
                        }
                    }
                }
                else {
                    var checkBox = document.getElementById("checkBox1," + ii.toString());
                    if (coverings == 0) { visible[i + total - h] = 1; }
					if(checkBox.innerHTML == ""){ checkBox.innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>"; }
					document.getElementById("cayleyText" + i.toString() + ".0").style.display = "block";
					document.getElementById("cayleyText0." + i.toString()).style.display = "block";
					for (var j = 0; j < h; j++) {
					    var cayleyRow = document.getElementById("cayleyCell" + i.toString() + "." + j.toString());
					    var cayleyColumn = document.getElementById("cayleyCell" + j.toString() + "." + i.toString());
						if (document.getElementById("cayleyText0." + j.toString()).style.display != "none" || j == 0) {
						    document.getElementById("cayleyText" + i.toString() + "." + j.toString()).style.display = "block";
						    cayleyRow.style.width = "1.5em";
						    cayleyRow.style.height = "1.5em";
						}
						if (document.getElementById("cayleyText" + j.toString() + ".0").style.display != "none" || j == 0) {
						    document.getElementById("cayleyText" + j.toString() + "." + i.toString()).style.display = "block";
						    cayleyColumn.style.width = "1.5em";
						    cayleyColumn.style.height = "1.5em";
						}
					}
					if (coverings == 0) {
					    setTimeout(function () {
					        for (var r = 0; r <= maxR; r++) {
					            var curvLayer = document.getElementById(r.toString());
					            for (var j = 0; j < total / h; j++) {
					                var layer = curvLayer.childNodes[h * j + i]; layer.style.visibility = "visible";
					                if (r == maxR && layer.childNodes.length == 0) { render(h * j + i); }
					            }
					        }
					    }, 10);
					}
                }
            }

            function highlight(i,j,k) {

				if(i == 6){
					if(k == 0){
					    var m = 2, jj = j + total - h;
						for(var l = 2; l < 5; l++){ if(styles[l][jj][7] % 2 == 1){ m = l; break;} }
						var color = "rgb(" + styles[m][jj][8].toString() + "," + styles[m][jj][9].toString() + "," + styles[m][jj][10].toString() + ")";
						document.getElementById("cayleyCell0." + j.toString()).style.backgroundColor = color;
						if(j != 0){
							document.getElementById("cayleyCell" + j.toString() + ".0").style.backgroundColor = color;
							for (var l = 1; l < h; l++) {
							    document.getElementById("cayleyCell" + l.toString() + "." + j.toString()).style.backgroundColor = "#c3cbd8";
							    document.getElementById("cayleyCell" + j.toString() + "." + l.toString()).style.backgroundColor = "#c3cbd8";
							}
						}

					}
					else{
						for (var l = 0; l < h; l++) {
						    document.getElementById("cayleyCell" + l.toString() + "." + j.toString()).style.backgroundColor = "white";
						    document.getElementById("cayleyCell" + j.toString() + "." + l.toString()).style.backgroundColor = "white";
						}
					}
					return;
				}

				if(i == 2){
					var element = 0; if(j > 1){ element = parseInt(document.getElementById("header3").getAttribute("data-value")); }
					if(styles[j][element][7] < 2){
						var swatch = document.getElementById("swatch" + j.toString());
						if(k == 0){ swatch.style.outlineStyle = "solid"; }
						else{ swatch.style.outlineStyle = "none"; }
					}
					return;
				}

				if(i == 3){
				    var cell = document.getElementById("td" + i.toString() + "," + j.toString());
					if(k == 0){
					    var m = 2; j += total - h;
					    if (j < 0) { cell.style.backgroundColor = "#c3cbd8"; }
					    else {
					        for (var l = 2; l < 5; l++) { if (styles[l][j][7] % 2 == 1) { m = l; break; } }
					        cell.style.backgroundColor = "rgb(" + styles[m][j][8].toString() + "," + styles[m][j][9].toString() + "," + styles[m][j][10].toString() + ")";
					    }
					}
					else { cell.style.backgroundColor = "white"; }
					return;
				}

				var cell = document.getElementById("td" + i.toString() + "," + j.toString());
				if(k == 0){ cell.style.backgroundColor = "#c3cbd8"; }
				else{ cell.style.backgroundColor = "white"; }
            }

            function option(i, j) {
					
                var header = document.getElementById("header" + i.toString());

                if (i <= 0) {
                    tog(1, i);
					if(j != normInd[total - h - i]){
						header.innerHTML = document.getElementById("option" + i.toString() + "," + j.toString()).innerHTML;
						normInd[total - h - i] = j; i *= -1;
						var principal = 1;
						for (var k = 0; k < reps[i][j].length - 1; k++) { principal *= reps[i][j][k]; }
						setTimeout(function () {
							for (var k = 0; k < h; ++k) {
							    var kk = reps[k][0][1], torsion = 1;
							    if (reps[kk][0][0] == -1) { kk -= 1; torsion = -1; }
							    if (kk == i) {
                                    var principal = 1, leng = reps[kk][j].length - 1;
							        if (reps[k][0][2] + 1 == d) { torsion *= reps[kk][j][leng] + d; }
							        else { torsion *= reps[k][0][2] * reps[kk][j][leng]; }
							        if (reps[kk][0][1] == 0 && (k > twoTor && (k - twoTor) % 2 == 1)) { torsion *= -1; }
							        for (var l = 0; l < leng; l++) { principal *= reps[kk][j][l]; }
							        prin[total - h + k] = Math.abs(principal); tor[total - h + k] = torsion;
							        if (i >= twoTor && (i - twoTor) % 2 != 0) { torsion *= -1; }
							        principal = two * two * Math.abs(principal);
							        var s = t = 0, norm = Math.sqrt(d / principal);
							        if (d == 1) { norm = 1; }
							        if (norm == parseInt(norm) && d != 1) { t = two * d; norm = parseInt(norm) * t; }
							        else {
							            norm = d * 16 / 9;
							            var ss = 1;
							            while (ss <= Math.sqrt(principal * norm)) {
							                if (ss % two == 0) { var tt = 0; }
							                else { var tt = 1; }
							                var bound = Math.sqrt((principal * norm - ss * ss) / d);
							                while (tt < bound) {
							                    var tempNorm = Math.sqrt((ss * ss + tt * tt * d) / principal);
							                    if (tempNorm == parseInt(tempNorm) && (parseInt(tempNorm) * torsion - ss) % (2 * d / two) == 0) { norm = parseInt(tempNorm); s = ss; t = tt; break; }
							                    tt *= -1; if (tt >= 0) { tt += two; }
							                }
							                ss *= -1; if (ss > 0) { ss++; }
							            }
							        }

							        if (k >= twoTor && (k - twoTor) % 2 != 0) { s *= -1; t *= -1; }
							        dets[total - h + k] = [s, t];
							        if (String(document.getElementById("cFrac").classList).indexOf("stayActive") == -1) { render(total - h + k); }
							        else { currentPrin = principal / (two * two); startingCover(); }
								}
							}
						}, 10);
					}
					return;
				}

                if(document.getElementById("toggle" + i.toString() + "," + i.toString()).style.display == "block"){ tog(i, i); }

				if (i == 3 && j != parseInt(header.getAttribute("data-value")) - total + h) {
				    header.innerHTML = document.getElementById("option3," + j.toString()).innerHTML;
				    if (j == -2) {
				        var infoTable = document.createElement("table");
				        infoTable.id = "infoTable"; notes.appendChild(infoTable);

				        for (var k = 0; k < selectCount; k++) {
				            if (document.getElementById("checkBox8," + k.toString())) { break; }
				            else {
				                var infoRow = document.createElement("tr");
				                infoRow.id = "row" + selectCount.toString();
				                var cell = document.createElement("td");
				                cell.style.width = "1.4em";
				                cell.style.paddingBottom = "0.5em";
				                var HTML = "<div class='checkBox' id='checkBox8," + k.toString() + "' onclick='check(8," + k.toString() + ")'>";
				                HTML += "<object class='checkmark' type='image/svg+xml' data='check.svg'></object></div>";
				                cell.innerHTML = HTML;
				                infoRow.appendChild(cell);
				                cell = document.createElement("td");
				                cell.style.paddingBottom = "0.5em";
				                cell.innerHTML = "whatever";
				                infoRow.appendChild(cell); document.getElementById("infoTable").appendChild(infoRow);
				            }
				        }

				        canvasContain.addEventListener("mousemove", infoHighlight);
				        canvas.addEventListener("mouseleave", infoRemove);
				        canvas.addEventListener("click", addSelect);
				        canvas.addEventListener("click", addSelect);
				        j = total;
				    }
				    else {
				        while (notes.lastChild) { notes.removeChild(notes.lastChild); }
				        canvasContain.removeEventListener("mousemove", infoHighlight);
				        canvas.removeEventListener("mouseleave", infoRemove);
				        canvas.removeEventListener("click", addSelect);
				        j += total - h;
				    }
				    var tempJ = header.getAttribute("data-value"), l = 0;
				    for (var k = 2; k < 5; k++) { if (styles[k][tempJ][7] > 1) { l = k; styles[k][tempJ][7] -= 2; styles[k][j][7] += 2; break; } }
					header.setAttribute("data-value", j);
					for(var k = 2; k < 5; k++){
						var checkBox = document.getElementById("checkBox3," + k.toString()), swatch = document.getElementById("swatch" + k.toString());
						if(styles[k][j][7] % 2 != 0){ if(checkBox.innerHTML == ""){ checkBox.innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>"; } }
						else{ checkBox.innerHTML = ""; }
						var color = styles[k][j][8].toString() + "," + styles[k][j][9].toString() + "," + styles[k][j][10].toString();
						document.getElementById("rgb" + k.toString()).value = color;
						swatch.style.backgroundColor = "rgb(" + color + ")";
						if(k == l){ setColors(k,j); }
					}
					return;
				}

                if (i == 5 && j != header.getAttribute("data-value")) {

					header.innerHTML = document.getElementById("option5," + j.toString()).innerHTML;
					header.setAttribute("data-value", j);
					var toggle = document.getElementById("toggle0,5");
					if(j > 3 && toggle.style.display == "none"){ toggle.style.display = "block"; }
					if(j < 4){ toggle.style.display = "none"; }
					return;
                }

                if (i == 7 || i == 8) {
                    header.innerHTML = document.getElementById("option" + i.toString() + "," + j.toString()).innerHTML;
                    header.setAttribute("data-value", j.toString());
                    if (i == 7) { var m1 = j, m2 = parseInt(document.getElementById("header8").getAttribute("data-value")); }
                    else { var m2 = j, m1 = parseInt(document.getElementById("header7").getAttribute("data-value")); }
                    var det1 = infoArray[m1][4], det2 = infoArray[m1][5];
                    norm = (det1 * det1 + d * det2 * det2) / (two * two);
                    var matrix1 = [infoArray[m1][14], infoArray[m1][15], -1 * infoArray[m1][10], -1 * infoArray[m1][11], -1 * infoArray[m1][12], -1 * infoArray[m1][13], infoArray[m1][8], infoArray[m1][9]], matrix2 = [];
                    for(var k = 8; k < 16; k++){ matrix2.push(infoArray[m2][k]); }
                    var tMatrix = matrixMult(matrix1, matrix2);
                    for (var k = 0; k < 8; k += 2) {
                        var temp = (tMatrix[k] * det1 + d * tMatrix[k + 1] * det2) / two;
                        tMatrix[k + 1] = (tMatrix[k + 1] * det1 - tMatrix[k] * det2) / two;
                        tMatrix[k] = (temp - (two - 1) * tMatrix[k + 1]) / two;
                    }

                    var gcd = 2;
                    while (gcd <= norm) {
                        var check = 0;
                        if (norm % gcd != 0) { check = 1; }
                        for (var k = 0; k < 8; k++) {
                            if (check == 1) { break; }
                            if (tMatrix[k] % gcd != 0) { check = 1; }
                        }
                        if (check == 0) {
                            norm /= gcd;
                            for (var k = 0; k < 8; k++) { tMatrix[k] /= gcd; }
                        }
                        else { gcd++; }
                    }
                    var detNorm = document.getElementById("detNorm");
                    if (norm == 1) { document.getElementById("detNorm").innerHTML = ""; }
                    else { document.getElementById("detNorm").innerHTML = norm.toString(); }
                    for (var k = 0; k < 4; k++) { document.getElementById("entry" + k.toString()).innerHTML = getEntry(tMatrix[2 * k], tMatrix[2 * k + 1]); }
                    var transition = document.getElementById("transition");
                    if (transition.style.display == "none") {
                        transition.style.display = "block";
                        var dlDiv = document.getElementById("dlDiv");
                        notes.style.maxHeight = String(dlDiv.offsetTop + dlDiv.offsetHeight - transition.offsetHeight - notes.offsetTop) + "px";
                    }
                }
            }

            function render(i) {

               var ii = reps[i % h][0][1];
					if(styles[2][i][7] % 2 == 0){ var color = "none"; }
					else { var color = "rgb(" + styles[2][i][8].toString() + "," + styles[2][i][9].toString() + "," + styles[2][i][10].toString() + ")"; }
					var color1 = "rgb(" + styles[2][1][8].toString() + "," + styles[2][1][9].toString() + "," + styles[2][1][10].toString() + ")";
					var color2 = "rgb(" + styles[2][2][8].toString() + "," + styles[2][2][9].toString() + "," + styles[2][2][10].toString() + ")";
					var backColor = "rgb(5,146,90)";


					var radii = [], principal = two * two * prin[i], torsion = tor[i];
					var thick = 0.003 * canvasWidth * (0.1 + 3 * styles[2][i][6]), sqrtp = Math.sqrt(principal) / sqrt;
					maxR = Math.floor(R * curvSet / canvasWidth); document.getElementById("curv").value = maxR.toString();

					var childCount = arrangement.childNodes.length;
					for (var k = maxR + 1; k < childCount; k++) { arrangement.removeChild(arrangement.lastChild); }
					var curvLayer = document.getElementById("0");
					if (curvLayer == null) { curvLayer = document.createElementNS(NS, "g"); curvLayer.id = "0"; arrangement.appendChild(curvLayer); }
					if (curvLayer.childNodes.length > i) { var layer = curvLayer.childNodes[i]; while (layer.lastChild) { layer.removeChild(layer.lastChild); } }
					else{
						var layer = document.createElementNS(NS, "svg");
						layer.setAttribute("width", maxWidth.toString());
						layer.setAttribute("height", maxWidth.toString());
						curvLayer.appendChild(layer);
					}

					var verts = [];
					if (visible[i] == 1) {
				   	var maxY = Math.floor(sqrtp * sqrt + 0.1), yVals = [];
				    	var startY = [torsion - 2 * d * Math.floor(two * (torsion + maxY) / (2 * d) + 0.5) / two];
				    	if (ii == 0 && (2 * torsion) % (2 * d / two) != 0) { startY.push(2 * d * Math.ceil(two * (torsion - maxY) / (2 * d)) / two - torsion); }
				    		for (var k = 0; k < startY.length; k++) {
				        		var y = startY[k];
				        		while (y <= maxY) {
				            	var minX = 0, maxX = Math.floor(sqrtp + 0.1), xVals = [y]; if (y < 0) { minX = 1; }
				            	for (var x = minX; x <= maxX; x++) {
				                	if (d * x * x + y * y == principal) {
				                    	if(y < 0){
				                        var minQ = Math.floor((x * sqrt * (originX - 2 * canvasWidth - canvasLeft) + y * (originY + canvasWidth - canvasTop)) / (scale * sqrt) + 0.1);
				                        var maxQ = Math.ceil((x * sqrt * (originX + canvasWidth - canvasLeft) + y * (originY - 2 * canvasWidth - canvasTop)) / (scale * sqrt) - 0.1);
				                    	}
				                    	else{
				                        var minQ = Math.floor((x * sqrt * (originX - 2 * canvasWidth - canvasLeft) + y * (originY - 2 * canvasWidth - canvasTop)) / (scale * sqrt) + 0.1);
				                        var maxQ = Math.ceil((x * sqrt * (originX + canvasWidth - canvasLeft) + y * (originY + canvasWidth - canvasTop)) / (scale * sqrt) - 0.1);
				                    	}
				                    	for(var q = minQ; q <= maxQ; q++){
				                        if(Math.abs(y) < sqrt * x){
				                        	var y1 = canvasTop + (renderWidth + 1) * canvasWidth / 2, x1 = originX + (y * (originY - y1) - q * scale * sqrt) / (sqrt * x);
				                           var y2 = canvasTop + (1 - renderWidth) * canvasWidth / 2, x2 = originX + (y * (originY - y2) - q * scale * sqrt) / (sqrt * x);
				                        }
				                        else{
				                           var x1 = canvasLeft + (1 - renderWidth) * canvasWidth / 2, y1 = originY + (x * sqrt * (originX - x1) - q * scale * sqrt) / y;
				                           var x2 = canvasLeft + (renderWidth + 1) * canvasWidth / 2, y2 = originY + (x * sqrt * (originX - x2) - q * scale * sqrt) / y;
				                        }
				                        var line = document.createElementNS(NS, "line");
				                        if (x == 0) { line.setAttribute("data-value", "x"); }
				                        if (y == 0) { line.setAttribute("data-value", "y"); }
				                        line.setAttribute("x1", x1); line.setAttribute("y1", y1);
				                        line.setAttribute("x2", x2); line.setAttribute("y2", y2);
												//normal												
												if(1 == 1){
				                        	line.setAttribute("stroke", color);
				                        	line.setAttribute("stroke-width", String(0.6*thick));
				                        	layer.appendChild(line);
				                        }												
												//Baragar-Lautzenheiser				                        
				                        if(1 == 0 && (q == 0 || q == -2) && (x+y) % 4 == 0){
				                        	verts.push([x1,y1,x2,y2]);
				                        }
												//Packing in S_8 for Delta=-23				                        
				                        if(1 == 0){
				                        	if(q % 2 == 0 && (x+y) % 4 == 0){
				                        		line.setAttribute("stroke", color);
				                        		line.setAttribute("stroke-width", String(0.8*thick));
				                        		layer.appendChild(line);
				                        	}
				                        }
				                        xVals.push(q);
				                    	}
				                     break;
				                	}
				            	}
				            	yVals.push(xVals);
				            	y += 2 * d / two;
				        		}
				    		}
				    	radii.push(yVals);
					}
					
					//job talk 6 rotate
					if(1 == 0){
						var line = document.createElementNS(NS, "line");
				      line.setAttribute("data-value", "y");
						line.setAttribute("x1", originX-3*scale); line.setAttribute("y1", originY-scale*0.5*(1+sqrt));
				   	line.setAttribute("x2", originX+3*scale); line.setAttribute("y2", originY-scale*0.5*(1+sqrt));
						line.setAttribute("stroke", color);
				   	line.setAttribute("stroke-width", String(0.6*thick));
				   	layer.appendChild(line);
				   	
				   	line = document.createElementNS(NS, "line");
				      line.setAttribute("data-value", "y");
						line.setAttribute("x1", originX-3*scale); line.setAttribute("y1", originY-scale*0.5*(sqrt-1));
				   	line.setAttribute("x2", originX+3*scale); line.setAttribute("y2", originY-scale*0.5*(sqrt-1));
						line.setAttribute("stroke", color);
				   	line.setAttribute("stroke-width", String(0.6*thick));
				   	layer.appendChild(line);
				   }
					var packing = [];
					for (var r = 1; r <= maxR; ++r) {

               	curvLayer = document.getElementById(r.toString());
                  if (curvLayer == null) { curvLayer = document.createElementNS(NS, "g"); curvLayer.id = r.toString(); arrangement.appendChild(curvLayer); }
                  if (curvLayer.childNodes.length > i) { var layer = curvLayer.childNodes[i]; while (layer.lastChild) { layer.removeChild(layer.lastChild); } }
						else{
							var layer = document.createElementNS(NS, "svg");
							layer.setAttribute("width", maxWidth.toString());
							layer.setAttribute("height", maxWidth.toString());
							curvLayer.appendChild(layer);
						}						
						
						if(visible[i] == 1){
					   	var yVals = [], rad = sqrtp / (2 * r);
					   	var minY = Math.ceil(2 * sqrt * r * (originY - canvasTop - (1 + renderWidth) * canvasWidth / 2) / scale - sqrt * sqrtp);
					   	var maxY = Math.floor(2 * sqrt * r * (originY - canvasTop + (renderWidth - 1) * canvasWidth / 2) / scale + sqrt * sqrtp);
					   	var minX = Math.ceil(2 * r * (canvasLeft - originX + (1 - renderWidth) * canvasWidth / 2) / scale - sqrtp);
					   	var maxX = Math.floor(2 * r * (canvasLeft - originX + (renderWidth + 1) * canvasWidth / 2) / scale + sqrtp);
					   	var startY = [torsion - 2 * d * Math.floor(two * (torsion - minY) / (2 * d) + 0.5) / two];
					   	if (ii == 0 && (2 * torsion) % (2 * d / two) != 0) { startY.push(2 * d * Math.ceil(two * (torsion + minY) / (2 * d)) / two - torsion); }
					   	for(var k = 0; k < startY.length; k++){
					   		var y = startY[k];
						  		while(y <= maxY){
									var centY = y / (2 * r * sqrt), xVals = [y];
							   	for(var x = minX; x <= maxX; x++){
							   	if ((d * x * x + y * y - principal) % (4 * d * r) == 0) {
							      	var q = (d * x * x + y * y - principal) / (4 * d * r);
                              var centX = x / (2*r);
							         var circle = document.createElementNS(NS, "circle");
							         circle.setAttribute("cx", String(originX + scale * centX));
							         circle.setAttribute("cy", String(originY - scale * centY));
							         circle.setAttribute("r", String(scale * rad));
							         circle.setAttribute("fill", "none");
										//normal							         
							         if(1 == 1){
							         	xVals.push(x);
							         	circle.setAttribute("stroke-width", String(0.6*thick));
							         	
							         	//job talk apollonius
							         	if(r == -1 || r == -15){
							         		circle.setAttribute("stroke", "rgb(193,3,1)");
							         	}
							         	else{
							         		if(r < 4000){
							         			circle.setAttribute("stroke", color);
							         		}
							         		else{ circle.setAttribute("stroke", "none"); }
							         	}
							         	
							         	//elementary for job talk
							         	if(centY < 0.52 || i != -1){ layer.appendChild(circle); }
							         }
										//strip packing							         
							         if(1 == 0){
							         	var appCheck = 0;
							         	if(centY > 0 && centY < 1){
							         		loopy: for(var c = 1; c < radii.length; c++){
							         			var radC = sqrtp / (2*c);
													for(var b = 0; b < radii[c].length; b++){
														var centB = radii[c][b][0] / (2*c*sqrt);	
														for(var a = 1; a < radii[c][b].length; a++){
															var centA = radii[c][b][a] / (2*c);
															if((centA-centX)*(centA-centX)+(centB-centY)*(centB-centY) <= radC*radC){
																appCheck = 1; break loopy;
															}													
														}													
													}							         		
							         		}
							         	}
							         	else{ appCheck = 1; }
							         	if(appCheck == 0){
							         		xVals.push(x);
							         		circle.setAttribute("stroke-width", String(0.8*thick));
							         		circle.setAttribute("stroke", "rgb(0,0,0)");
							         		layer.appendChild(circle);
							         		var mult = 0.06;
							         		if(r >= 10){ mult = 0.042; }
							         		if(r >= 100){ mult = 0.028; }
							         		var newText = document.createElementNS(NS, "text");
							         		newText.setAttribute("x",String(originX + scale * (centX + 0.05)));     
												newText.setAttribute("y",String(originY - scale * (centY - 0.05))); 
												newText.setAttribute("font-size",String(canvasWidth*mult*16/r));
												newText.setAttribute("text-anchor","middle");
												newText.setAttribute("alignment-baseline","central");
												newText.setAttribute("fill","rgb(0,0,0)");
												var textNode = document.createTextNode(r.toString());
												newText.appendChild(textNode);
												layer.appendChild(newText);
							         	}
							         }
										//-1, 2, 2, 3 packing
										if(1 == 0){
							         	var appCheck = 0;
							         	if(centX*centX + (centY-0.5)*(centY-0.5) < 0.25){
							         		loopy: for(var c = 2; c < radii.length; c++){
							         			var radC = sqrtp / (2*c);
													for(var b = 0; b < radii[c].length; b++){
														var centB = radii[c][b][0] / (2*c*sqrt);	
														for(var a = 1; a < radii[c][b].length; a++){
															var centA = radii[c][b][a] / (2*c);
															if((centA-centX)*(centA-centX)+(centB-centY)*(centB-centY) <= radC*radC){
																appCheck = 1; break loopy;
															}													
														}													
													}							         		
							         		}
							         	}
							         	else{ appCheck = 1; }
							         	if(appCheck == 0){
							         		xVals.push(x);
							         		packing.push([centX,centY,rad]);
							         		if(1 == 0 && (r == 2 || (r == 3 && centX > 0) || (r == 15 && centX > 0 && centY == 0.5))){
							         			var mult = 0.05;
							         			if(r >= 10){ mult = 0.035; }
							         			if(r >= 100){ mult = 0.022; }
							         			var newText = document.createElementNS(NS, "text");
							         			newText.setAttribute("x",String(originX + scale * (centX)));     
													newText.setAttribute("y",String(originY - scale * (centY))); 
													newText.setAttribute("font-size",String(canvasWidth*mult*16/r));
													newText.setAttribute("text-anchor","middle");
													newText.setAttribute("alignment-baseline","central");
													newText.setAttribute("fill","rgb(0,0,0)");
													var textNode = document.createTextNode(r.toString());
													newText.appendChild(textNode);
													layer.appendChild(newText);
												}
												if(r == 1 && 1 == 0){
													var mult = 0.01;
							         			var newText = document.createElementNS(NS, "text");
							         			newText.setAttribute("x",String(originX + scale * 0.4));     
													newText.setAttribute("y",String(originY - scale * 0.93)); 
													newText.setAttribute("font-size",String(canvasWidth*mult*16/r));
													newText.setAttribute("text-anchor","middle");
													newText.setAttribute("alignment-baseline","central");
													newText.setAttribute("fill","rgb(0,0,0)");
													var textNode = document.createTextNode("-1");
													newText.appendChild(textNode);
													layer.appendChild(newText);
												}
							         	}
							         	else{
												xVals.push(x);
							         		circle.setAttribute("stroke-width", String(0.6*thick));
							         		circle.setAttribute("stroke", color);
							         		layer.appendChild(circle);							         	
							         	}
							         }							         
							         
							         //Packing in S_8 for Delta=-23
							         if (1 == 0 && (x-y) % 2 == 0 && q % 2 != 0) { 
							         	var pack = -1;
							         	if(centY > -1*sqrt*centX && centY < -1*sqrt*(centX-2)){
							         		pack = 1;
							         		for(var l = 0; l < packing.length; l++){
													if(Math.pow(centX-packing[l][0],2)+Math.pow(centY-packing[l][1],2)<Math.pow(packing[l][2],2)){
														pack = -1; break;
													}											
												}
							         	}
							         	if(pack == -1){
												packing.push([centX,centY,rad]);						         
							        	 	}
							         	else{ 
							         		circle.setAttribute("stroke", "rgb(180,180,180)"); 
							         		circle.setAttribute("stroke-width", String(0.5*thick)); 
							         		layer.appendChild(circle);
							         	}
							         }
							         //Baragar-Lautzenheiser
							         if(1 == 0){
							         	var pack = -1;
							         	demo.innerHTML = d;
							         	if(d == 1 && (0 < centX && 1 > centX) && (q % 2 == 0 && r % 2 == 0 && y % 8 == 0)){				         	
							         		pack = 1;
												for(var l = 0; l < packing.length; l++){
													if(Math.pow(centX-packing[l][0],2)+Math.pow(centY-packing[l][1],2)<Math.pow(packing[l][2],2)){
														pack = -1; break;
													}											
												}							         
							         	}
							         	if(d == 5 && (0 < centX && 1 > centX) && (y % 10 == 0)){				         	
							         		pack = 1;
												for(var l = 0; l < packing.length; l++){
													if(Math.pow(centX-packing[l][0],2)+Math.pow(centY-packing[l][1],2)<Math.pow(packing[l][2],2)){
														pack = -1; break;
													}											
												}							         
							         	}
							         	if((d != 1 && d != 5) && (0 < centX && 1 > centX)){				         	
							         		pack = 1;
												for(var l = 0; l < packing.length; l++){
													if(Math.pow(centX-packing[l][0],2)+Math.pow(centY-packing[l][1],2)<Math.pow(packing[l][2],2)){
														pack = -1; break;
													}											
												}							         
							         	}
							         	if(pack == 1){
												packing.push([centX,centY,rad,r]);						         
							        	 	}
							         	else{ 
							         		var cX = centY - 0.5*(sqrt-1);
							         		var cY = 0.5*(1+sqrt) - centX;
							         		circle.setAttribute("cx", String(originX + scale * cX));
							         		circle.setAttribute("cy", String(originY - scale * cY));
							         		circle.setAttribute("stroke", "rgb(180,180,180)"); 
							         		circle.setAttribute("stroke-width", String(0.5*thick)); 
							         		if(1 == 0){ layer.appendChild(circle); }
							         	}
							         }					         
							         if(1 == 0) {
							         	if ((x - y) % 4 == 0 && x % 2 == 0) {
							            	if (r % 2 == 0) {
							               	if (q % 2 == 0) {
							                  	circle.setAttribute("stroke", "rgb(4,38,230)");
							                  }
							                  else {
							                  	circle.setAttribute("stroke", "rgb(119,5,152)");
							                  }
							               }
							         		else {
							        				if (q % 2 == 0) {
							               		circle.setAttribute("stroke", "rgb(255,197,8)");
							               	}
							            	}
							        		}
							            else {
							           		if (((y - x) / 2 - r) % 2 == 0 && (((y + x) / 2 + q) % 2 == 0 && x % 2 == 0)) {
							               	circle.setAttribute("stroke", "rgb(7,166,208)");
							               }
							               else {
							                  if (((r % 2 == 0) && (x + y) % 4 == 0) && (x + q) % 2 == 0) {
							                  	circle.setAttribute("stroke", "rgb(232,0,23)");
							                  }
							                  else {
							                  	if (((r % 2 == 0) && (x - y) % 4 == 0) && (x + q) % 2 == 0) {
							                     	circle.setAttribute("stroke", "rgb(241,107,8)");
							                     }
							                     else {
							                     	if (q % 2 == 0 && ((y - x) % 4 == 0 && ((x + r) % 2 == 0))) {
							                        	circle.setAttribute("stroke", "rgb(227,61,128)");
							                        }
							                        else {
							                        	if ((r % 2 == 0 && q % 2 == 0) && (y - x) % 4 == 0) {
							                           	circle.setAttribute("stroke", "rgb(152, 156, 197)");
							                           }
							                           else {
							                           	if ((r % 2 == 0 && q % 2 == 0) && (y + x) % 4 == 0) {
							                              	circle.setAttribute("stroke", "rgb(169,91,76)");
							                              }
							                              else {
							                              	if (q % 2 == 0 && ((y + x) % 4 == 0 && ((x - r) % 2 == 0))) {
							                                 	circle.setAttribute("stroke", "rgb(5,120,15)");
							                                 }
							                              }
							                         	}
							                        }
							                   	}
							                 	}
							          		}
							      		}
							    		}
							         if(1 == 0){
							         	var poly = (d*(x+10)*(x+10) + (y-2)*(y-2) - principal) / (4*d);
							         	var newText = document.createElementNS(NS, "text");
							         	newText.setAttribute("x",String(originX + scale * x / (2 * r)));     
											newText.setAttribute("y",String(originY - scale * centY)); 
											newText.setAttribute("font-size",String(canvasWidth*0.036));
											newText.setAttribute("text-anchor","middle");
											newText.setAttribute("alignment-baseline","central");
											if(poly % 12 == 0){ newText.setAttribute("fill","rgb(0,0,0)"); }
											else{ newText.setAttribute("fill","rgb(170,170,170)"); }
											var textNode = document.createTextNode(poly.toString());
											newText.appendChild(textNode);
											layer.appendChild(newText);
							         }
							   	}
							 	}
							   	yVals.push(xVals);
							   	y += 2 * d / two;
								}
							}
							radii.push(yVals);
						}
          		}
               if (i >= total - h) { circArray[i % h] = radii; }
               if (visible[i] == 1) { for (var k = 3; k < 5; k++) { if (styles[k][i][7] % 2 == 1) { styling(k, i); } } }
					//something in Delta = -19					
					if(1 == 0){					
						var circle = document.createElementNS(NS, "circle");
						circle.setAttribute("cx", String(originX + scale * 7/34));
						circle.setAttribute("cy", String(originY + scale * Math.sqrt(19)/34));
						circle.setAttribute("r", String(scale * 0.02));
						circle.setAttribute("fill", "rgb(250,0,0)");
						circle.setAttribute("stroke", "none");
						canvas.appendChild(circle);
					}

               if (1 == 0) {
               	curvLayer = document.getElementById("extra");
                  if (curvLayer == null) {
                  	curvLayer = document.createElementNS(NS, "g"); curvLayer.id = "extra";
                  	arrangement.appendChild(curvLayer);
                  	var layer = document.createElementNS(NS, "svg");
                  	layer.setAttribute("width", maxWidth.toString());
                  	layer.setAttribute("height", maxWidth.toString());
                  	curvLayer.appendChild(layer);
               	}
               	else {
               		var layer = curvLayer.childNodes[0];
                  	while (layer.lastChild) { layer.removeChild(layer.lastChild); }
               	}

               	for (var i = -1; i < 4; i++) {
               		for (j = 0; j < 2; j++) {
                  		var centX = i - j / 2;
                     	var centY = j * Math.sqrt(d) / two;
                     	var circle = document.createElementNS(NS, "circle");
                     	circle.setAttribute("cx", String(originX + scale * centX));
                     	circle.setAttribute("cy", String(originY - scale * centY));
                     	circle.setAttribute("r", String(scale));
                     	circle.setAttribute("fill", "rgba(4,38,210,0.5)");
                     	circle.setAttribute("stroke-width", String(canvasWidth / 1000));
                     	circle.setAttribute("stroke", "rgb(0,0,0)");
                     	layer.appendChild(circle);
                		}
            		}
         		}
         		//packings
         		if(1 == 0){
               	for(var k = 0; k < verts.length; k++){
               		var line = document.createElementNS(NS, "line");
               		line.setAttribute("data-value", "y");
				      	line.setAttribute("x1", verts[k][0]); line.setAttribute("y1", verts[k][1]);
				      	line.setAttribute("x2", verts[k][2]); line.setAttribute("y2", verts[k][3]);
				      	line.setAttribute("stroke", "rgb(0,0,0)");
				      	line.setAttribute("stroke-width", String(0.6*thick));
				      	layer.appendChild(line);
               	}
               	//Packing in S_8 for Delta=-23
               	if(1 == 0 && i == 0){ packing.push([1.25,3.25/sqrt,sqrtp/8]); }
               	
               	for(var k = 0; k < packing.length; k++){
               		var circle = document.createElementNS(NS, "circle");
							circle.setAttribute("cx", String(originX + scale * packing[k][0]));
							circle.setAttribute("cy", String(originY - scale * packing[k][1]));
							circle.setAttribute("r", String(scale * packing[k][2]));
							circle.setAttribute("fill", "none");
							circle.setAttribute("stroke-width", 1.6*thick);
							circle.setAttribute("stroke", "rgb(0,0,0)");
							layer.appendChild(circle);
							if(1 == 0){
								var mult = 0.02;
							   if(packing[k][3] >= 10){ mult = 0.014; }
							   if(packing[k][3] >= 100){ mult = 0.0085; }
							   var newText = document.createElementNS(NS, "text");
							   newText.setAttribute("x",String(originX + scale * (cX)));     
								newText.setAttribute("y",String(originY - scale * (cY))); 
								newText.setAttribute("font-size",String(canvasWidth*mult*16/packing[k][3]));
								newText.setAttribute("text-anchor","middle");
								newText.setAttribute("alignment-baseline","central");
								newText.setAttribute("fill","rgb(0,0,0)");
								var textNode = document.createTextNode(packing[k][3].toString());
								newText.appendChild(textNode);
								layer.appendChild(newText);
							}
						}
					}
					//gaps in uncovered points
					if(1 == 0 && i == 0){
						var qBound = 1000;
						for(var q = 2; q < qBound; q++){
							var miniX = Math.floor(0.05*q);
							var maxiX = Math.floor(0.45*q);
							var miniY = Math.floor(1.5*q/Math.sqrt(39));
							var maxiY = Math.floor(1.9*q/Math.sqrt(39));
							for(var xx = miniX; xx <= maxiX; xx++){
								for(var yy = miniY; yy <= maxiY; yy++){
									var GCD = getGcd(getGcd(xx,yy),q);
									if(GCD == 1){
										var NORM = getNormGcd(two*xx,two*yy,two*q,0);
										NORM = q*q/NORM;
										if(NORM <= 540){
											var temp = NORM;
											while(temp % 39 == 0){ temp /= 39; }
											var square = 0;
											for(var nn = 0; nn < 39; nn++){
												if((nn*nn-temp) % 39 == 0){
													square = 1; break;												
												}											
											}
											if(square == 0){
												var circle = document.createElementNS(NS, "circle");
               							circle.setAttribute("cx", String(originX + scale * xx / q));
												circle.setAttribute("cy", String(originY - scale * sqrt * yy / q));
												circle.setAttribute("r", String((Math.sqrt(2)-1)*scale*Math.min(1/Math.sqrt(2 * maxR * NORM),1/NORM)));
												circle.setAttribute("fill", "rgb(179,64,55)");
												circle.setAttribute("stroke-width", 1.0*thick);
												circle.setAttribute("stroke", "none");
												layer.appendChild(circle);											
											}										
										}									
									}						
								}							
							}						
						}
					}
			}

            function draw() {
                document.body.classList.add("wait"); waitWrap.classList.add("disable");
                if (String(document.getElementById("info").classList).indexOf("stayActive") > -1) { info(); }
                if (String(document.getElementById("cFrac").classList).indexOf("stayActive") > -1) { cFrac(); }
                maxWidth = 1700; initWidth = 116.666;

                setTimeout(function () {

                    zoomPan -= 20;
                    //check for good inputs
                    var dTemp = document.getElementById("disc").value;
                    if (dTemp == parseInt(dTemp)) {
                        dTemp = parseInt(dTemp);
                        var i = 2;
                        while (i <= dTemp) {
                            if (dTemp % (i * i) == 0) { dTemp = dTemp / (i * i); }
                            else { i++; }
                        }
                        if (dTemp <= 0 || dTemp >= 100) { return; }
                    }
                    else { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); return; }

                    if (d != dTemp) {

                        d = dTemp; sqrt = Math.sqrt(d);
                        
                        if ((d - 3) % 4 == 0) { two = 2; }
                        else { two = 1; }
                        if (sqrt * 2 < two * (two + 1)) {
                            scale = 200 / (two + 1); originX = (maxWidth - initWidth) / 2; originY = maxWidth / 2 + scale * sqrt / (2 * two);
                        }
                        else { scale = initWidth * two / (1.1666*sqrt); originX = maxWidth / 2 - scale * (two + 1) / 4; originY = (maxWidth + initWidth - 16.666) / 2; }
                        
                        if(1 == 0){  
									//for job talk in Q(sqrt(-23))
									scale = initWidth/1.25; originX = (maxWidth)/2-0.29*scale; originY = maxWidth/2+scale*0.388;   
									
									//for job talk in Q(sqrt(-1))
									scale = initWidth/1.1666; originX = maxWidth / 2; originY = (maxWidth + initWidth - 16.666) / 2;             
                        }
                        circArray = []; reps = []; normInd = []; styles = []; R = Math.floor(26.5 - 2 * sqrt / two); visible = []; curvSet = initWidth; prin = []; tor = []; dets = []; infoArray = []; selectArray = [];
                        background.setAttribute("fill", "none"); canvasWidth = initWidth; canvasLeft = canvasTop = (maxWidth - initWidth) / 2; delta = initWidth / containWidth; infoCount = 0; selectCount = 0; selectLabelCount = 0;
                        canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + initWidth.toString() + " " + initWidth.toString());
                        while (elementList.lastChild) { elementList.removeChild(elementList.lastChild); }
                        while (menu.lastChild) { menu.removeChild(menu.lastChild); }
                        while (cayley.lastChild) { cayley.removeChild(cayley.lastChild); }
                        while (structure.lastChild) { structure.removeChild(structure.lastChild); }
                        while (notes.lastChild) { notes.removeChild(notes.lastChild); }
                        while (arrangement.lastChild) { arrangement.removeChild(arrangement.lastChild); }
                        while (selectCircles.lastChild) { selectCircles.removeChild(selectCircles.lastChild); }
                        while (selectLabels.lastChild) { selectLabels.removeChild(selectLabels.lastChild); }
                        while (infoLabels.lastChild) { infoLabels.removeChild(infoLabels.lastChild); }
                        while (viewer.lastChild) { viewer.removeChild(viewer.lastChild); }
                        if (String(document.getElementById("info").classList).indexOf("stayActive") > -1) { info(); }
                        else {
                            while (infoCircles.lastChild) { infoCircles.removeChild(infoCircles.lastChild); }
                            canvasContain.removeEventListener("mousemove", infoHighlight);
                            canvas.removeEventListener("mouseleave", infoRemove);
                        }
                        loop: for (var i = 0; i < canvas.childNodes.length; i++) {
                            var element = canvas.childNodes[i];
                            if (element.id) {
                                if (element.id == "blurHL") { break loop; }
                                canvas.removeChild(element);
                            }
                        }
                        canvas.removeEventListener("click", addSelect);

                        for (var i = 2; i < 4; i++) {
                            var array = [3, 5];
                            for (var j = 0; j < array[i - 2]; j++) {
                                var checkBox = document.getElementById("checkBox" + i.toString() + "," + j.toString());
                                if ((i == 2 && j == 0) || (i == 3 && j == 2)) { checkBox.innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>"; }
                                else { checkBox.innerHTML = ""; }
                            }
                        }

                        //get CSV data
                        var n = 0; var data = [];
                        while(n < dataArray.length){
                        	if(dataArray[n][0] == d){ 
                        		for(var j = 1; j < dataArray[n].length; j++){
											data.push(dataArray[n][j]);                        		
                        		}
										break;                        	
                        	}
                        	n++;
                        }
                        if(n == dataArray.length){ return; }
                        var array = []; n = 0;
								
                        var caytab = [], factors = [];
                        h = data[0], total = h, n = 3, twoTor = data[1];
                        for (var i = 0; i < h; i++) { circArray.push([]); }
                        while (n < 3 + data[2]) { factors.push(data[n]); ++n; }
                        while (n < 3 + data[2] + h * h) {
                            var tempArray = [];
                            for (var i = 0; i < h; i++) { tempArray.push(data[n]); n++; }
                            caytab.push(tempArray);
                        }
                        for (var i = 0; i < h; i++) {
                            visible.push(1);
                            var vals = []; var tempArray = [];
                            tempArray.push(data[n], data[n + 1], data[n + 2]);
                            vals.push(tempArray); n = n + 3;
                            for (var j = 2; j < 5; ++j) {
                                var length = data[n]; n++;
                                for (var k = 0; k < length / j; k++) {
                                    tempArray = [];
                                    for (var l = 0; l < j; l++) { tempArray.push(data[n]); n++; }
                                    vals.push(tempArray);
                                }
                            }
                            reps.push(vals);
                        }



                        //give group structure
                        structure.innerHTML = "&#x1d436;<sub class='subScript'>" + factors[0].toString() + "</sub>";
                        for (var i = 1; i < factors.length; i++) {
                            structure.innerHTML += "&#215;&#x1d436;<sub class='subScript'>" + factors[i].toString() + "</sub>";
                        }


                        //create element list
                        var elements = ["&#x1d452;"]
                        for (var i = 1; i < h; ++i) {
                            if (i < twoTor) { elements.push("&#x1d44e;<sub class='subScript'>" + i.toString() + "</sub>"); }
                            else {
                                if ((i - twoTor) % 2 == 0) {
                                    var ii = twoTor + (i - twoTor) / 2;
                                    elements.push("&#x1d44e;<sub class='subScript'>" + ii.toString() + "</sub>");
                                }
                                else {
                                    var ii = twoTor + (i - twoTor - 1) / 2;
                                    elements.push("&#x1d44e;<sub class='subScript'>" + ii.toString() + "</sub><sup class='superScript'>-1</sup>");
                                }
                            }
                        }

                        //create style list
                        var table = document.createElement("table");
                        table.className = "table4";
                        table.style.position = "absolute";
                        table.style.top = "0";
                        table.style.left = "0";
                        table.style.zIndex = "1";
                        var row = document.createElement("tr");
                        var HTML = "<th onclick='tog(3,3)'><div id='header3' data-value='0' style='width:3.3em;height:1.3em;'>";
                        HTML += "&#x1d452;</div><img src='downarrow.jpg' class='arrow' id='arrow3,3'></th>";
                        row.innerHTML = HTML;
                        table.appendChild(row);
                        var body = document.createElement("tbody");
                        body.style.display = "none";
                        body.id = "toggle3,3";
                        for (var i = 0; i < h; i++) {
                            row = document.createElement("tr");
                            HTML = "<td id='td3," + i.toString() + "' onclick='option(3," + i.toString() + ")' onmouseover='highlight(3," + i.toString() + ",0)' onmouseout='highlight(3," + i.toString() + ",1)'>";
                            HTML += "<div id='option3," + i.toString() + "' style='width:3.3em;height:1.3em;'>" + elements[i] + "</div></td>";
                            row.innerHTML = HTML; body.appendChild(row);
                        }
                        for (var i = -2; i < 0; i++) {
                            row = document.createElement("tr");
                            HTML = "<td id='td3," + i.toString() + "' onclick='option(3," + i.toString() + ")' onmouseover='highlight(3," + i.toString() + ",0)' onmouseout='highlight(3," + i.toString() + ",1)'>";
                            HTML += "<div id='option3," + i.toString() + "' style='width:3.3em;height:1.3em;'>"
                            if (i == -2) { HTML += "select</div></td>"; }
                            else { HTML += "label</div></td>"; }
                            row.innerHTML = HTML; body.appendChild(row);
                        }
                        table.appendChild(body); elementList.appendChild(table);



                        //create Cayley table
                        table = document.createElement("table"); table.className = "table1";
                        for (var i = 0; i < h; i++) {
                            row = document.createElement("tr"); HTML = "";
                            for (var j = 0; j < h; j++) {
                                HTML += "<td id='cayleyCell" + i.toString() + "." + j.toString() + "'";
                                if (j == 0 || i == 0) {
                                    var k = Math.max(i, j);
                                    HTML += " onclick='collapse(" + k.toString() + ")' onmouseover='highlight(6," + k.toString() + ",0)' onmouseout='highlight(6," + k.toString() + ",1)'>"
                                }
                                else { HTML += ">"; }
                                HTML += "<div id='cayleyText" + i.toString() + "." + j.toString() + "' style='pointer-events:none;'>" + elements[caytab[i][j]] + "</div></td>";
                            }
                            row.innerHTML = HTML; table.appendChild(row);
                        }
                        cayley.appendChild(table);




                        //Create ideal options
                        table = document.createElement("table");
                        table.className = "table2";
                        for (var i = 0; i < h; i++) {
                            if (reps[i][0][0] == 1) {
                                row = document.createElement("tr");
                                if (i != 0) {
                                    row.style.height = "0.4em";
                                    table.appendChild(row);
                                    row = document.createElement("tr");
                                }
                                var cell = document.createElement("td");
                                cell.style.width = "1.4em";
                                HTML = "<div class='checkBox' id='checkBox1," + i.toString() + "' onclick='check(1," + i.toString() + ")'>";
                                HTML += "<object class='checkmark' type='image/svg+xml' data='check.svg'></object></div>";
                                cell.innerHTML = HTML;
                                row.appendChild(cell);
                                cell = document.createElement("td");
                                cell.style.width = "3em";
                                HTML = "[" + elements[i] + "]:"
                                cell.innerHTML = HTML;
                                row.appendChild(cell);
                                cell = document.createElement("td");
                                var innerTab = document.createElement("table");
                                innerTab.className = "table4";
                                innerTab.style.zIndex = String(h - i);
                                innerTab.style.position = "absolute";
                                innerTab.style.top = "-1px";
                                innerTab.style.left = "0";
                                var innerRow = document.createElement("tr");
                                var innerBody = document.createElement("tbody");
                                innerBody.style.display = "none"
                                HTML = "<th onclick='tog(1," + String(-1 * i) + ")'><div id='header" + String(-1 * i) + "' style='width:3.3em;height:1.3em;'>";
                                var start = 1;
                                if (i == 0) {
                                    HTML += "&#x1d4aa;<sub class='subScript'>K</sub></div><img src='downarrow.jpg' class='arrow' id='arrow1,0'></th>";
                                    innerRow.innerHTML = HTML;
                                    innerTab.appendChild(innerRow);
                                    innerRow = document.createElement("tr");
                                    innerBody.id = "toggle1,0";
                                    HTML = "<td id='td0,1' onclick='option(0,1)' onmouseover='highlight(0,1,0)' onmouseout='highlight(0,1,1)'>";
                                    HTML += "<div id='option0,1' style='width:3.3em;height:1.3em;'>&#x1d4aa;<sub class='subScript'>K</sub></div></td>";
                                    innerRow.innerHTML = HTML;
                                    innerBody.appendChild(innerRow);
                                    start = 2;
                                }
                                else {
                                    if (reps[i][1][0] < 0) {
                                        HTML += "<span style='text-decoration:overline'>&#x1d52d;</span><sub class='subScript'>" + Math.abs(reps[i][1][0]).toString() + "</sub>";
                                    }
                                    else {
                                        HTML += "&#x1d52d;<sub class='subScript'>" + reps[i][1][0].toString() + "</sub>";
                                    }
                                    HTML += "</div><img src='downarrow.jpg' class='arrow' id='arrow1," + String(-1 * i) + "'></th>";
                                    innerRow.innerHTML = HTML;
                                    innerTab.appendChild(innerRow);
                                    innerBody.id = "toggle1," + String(-1 * i);
                                }

                                for (var j = start; j < reps[i].length; j++) {
                                    innerRow = document.createElement("tr");
                                    var leng = reps[i][j].length - 1;
                                    HTML = "<td id='td" + String(-1 * i) + "," + j.toString() + "' onclick='option(" + String(-1 * i) + "," + j.toString() + ")' onmouseover='highlight(" + String(-1 * i) + "," + j.toString() + ",0)' ";
                                    HTML += "onmouseout='highlight(" + String(-1 * i) + "," + j.toString() + ",1)'><div id='option" + String(-1 * i) + "," + j.toString() + "' style='width:3.3em;height:1.3em;'>"
                                    var exp = 1;
                                    for (var k = 0; k < leng; k++) {
                                        if (k + 1 < leng) {
                                            if (reps[i][j][k] == reps[i][j][k + 1]) { ++exp; }
                                            else {
                                                if (reps[i][j][k] < 0) { HTML += "<span class='overline'>&#x1d52d;</span>"; }
                                                else { HTML += "&#x1d52d;"; }
                                                HTML += "<sub class='subScript'>" + Math.abs(reps[i][j][k]).toString() + "</sub>";
                                                if (exp != 1) { HTML += "<sup class='superScript'>" + exp.toString() + "</sup>"; }
                                                exp = 1;
                                            }
                                        }
                                        else {
                                            if (reps[i][j][k] < 0) { HTML += "<span class='overline'>&#x1d52d;</span>"; }
                                            else { HTML += "&#x1d52d;"; }
                                            HTML += "<sub class='subScript'>" + Math.abs(reps[i][j][k]).toString() + "</sub>";
                                            if (exp != 1) { HTML += "<sup class='superScript'>" + exp.toString() + "</sup>"; }
                                        }
                                    }
                                    HTML += "</div></td>";
                                    innerRow.innerHTML = HTML;
                                    innerBody.appendChild(innerRow);
                                }
                                innerTab.appendChild(innerBody);
                                cell.appendChild(innerTab);
                                row.appendChild(cell);
                                table.appendChild(row);
                            }
                        }
                        menu.appendChild(table);


                        //start styles
                        styles = [];
                        var alphas = [0.12, 1];
                        for (var i = 0; i < 2; i++) {
                            var styleArray = [[255, 255, 255, 0, 68, 66, alphas[i], 0, 0, 0, 0]];
                            styles.push(styleArray);
                            var swatch = document.getElementById("swatch" + i.toString());
                            swatch.style.backgroundColor = "rgb(0,0,0)";
                            swatch.style.outlineOffset = "0";
                            swatch.style.outlineStyle = "none";
                            document.getElementById("rgb" + i.toString()).value = "0,0,0";
                        }
                        styles.push([[255, 255, 255, 0, 68, 66, 0.12, 0, 0, 0, 0], [255, 255, 255, 0, 68, 66, 0.12, 1, 0, 0, 0]]);
                        styles.push([[255, 255, 255, 0, 68, 66, 0, 0, 0, 0, 0], [255, 255, 255, 1, 68, 66, 1, 1, 255, 255, 255]]);
                        styles.push([[255, 255, 255, 0, 68, 66, 0, 0, 0, 0, 0], [255, 255, 255, 0, 68, 66, 0.8, 1, 0, 0, 0]]);
                    }

                    else {
                        for (var i = 0; i < h; i++) {
                            visible.push(visible[i]);
                            if (reps[i][0][0] == 1) {
                                document.getElementById("header" + String(-1 * i)).innerHTML = document.getElementById("option" + String(-1 * i) + ",1").innerHTML;
                            }
                        }
                        total += h;
                        var header = document.getElementById("header3");
                        header.setAttribute("data-value", String(total - h));
                        header.innerHTML = document.getElementById("option3,0").innerHTML;
                        document.getElementById("checkBox3,2").innerHTML = "<object class='checkmark' type='image/svg+xml' data='check.svg'></object>";
                        for (var i = 3; i < 5; i++) { document.getElementById("checkBox3," + i.toString()).innerHTML = ""; }
                    }


                    //set styles
                    var alphas = [0.18, 0.3, 1];
                    for (var i = 2; i < 5; i++) {
                        for (var j = 0; j < h; j++) {
                            var styleArray = getStyleArray(col[j][0], col[j][1], col[j][2]);
                            styleArray.push(alphas[i - 2]);
                            var tempArray = styleArray.slice(0);
                            if (i == 2) { tempArray.push(1); }
                            else { tempArray.push(0); }
                            for (var k = 0; k < 3; k++) { tempArray.push(Math.floor(styleArray[k] * styleArray[3] + 0.5)); }
                            styles[i].splice(total - h + j, 0, tempArray);
                        }
                        var swatch = document.getElementById("swatch" + i.toString());
                        swatch.style.backgroundColor = "rgb(" + col[0][0] + "," + col[0][1] + "," + col[0][2] + ")";
                        swatch.style.outlineOffset = "0";
                        swatch.style.outlineStyle = "none";
                        document.getElementById("rgb" + i.toString()).value = col[0][0] + "," + col[0][1] + "," + col[0][2];
                    }

                    for (var i = 0; i < h; i++) {
                        var filter = document.createElementNS(NS, "filter");
                        filter.id = "blurFilter" + String(total - h + i);
                        filter.setAttribute("x", "-200%"); filter.setAttribute("y", "-200%");
                        filter.setAttribute("width", "500%"); filter.setAttribute("height", "500%");
                        filter.innerHTML = "<feGaussianBlur id='stdDev" + String(total - h + i) + "' in='SourceGraphic' stdDeviation='" + String(canvasWidth * (0.004 + 0.003 * alphas[2])) + "' />";
                        canvas.insertBefore(filter, canvas.childNodes[0]);
                    }

                    //reset toggles
                    for (var i = 1; i < 4; i++) {
                        var toggle = document.getElementById("toggle0," + i.toString());
                        if (toggle != null) {
                            if (document.getElementById("toggle0," + i.toString()).style.display != "none") {
                                document.getElementById("toggle0," + i.toString()).style.display = "none";
                                document.getElementById("arrow0," + i.toString()).src = "downarrow.jpg";
                            }
                        }
                    }
                    for (var i = 6; i < 9; i++) {
                        document.getElementById("toggle0," + i.toString()).style.display = "block";
                        document.getElementById("arrow0," + i.toString()).src = "uparrow.jpg";
                    }
                    document.getElementById("toggleColors").style.display = "none";
                    document.getElementById("toggleAlpha").style.display = "none";


                    for (var i = 0; i < h; i++) {
                        normInd.push(1);
                        var ii = reps[i][0][1], principal = torsion = 1;
                        if (reps[ii][0][0] == -1) { ii -= 1; torsion = -1; }
                        var leng = reps[ii][1].length - 1;
                        if (reps[i][0][2] + 1 == d) { torsion *= reps[ii][1][leng] + d; }
                        else { torsion *= reps[i][0][2] * reps[ii][1][leng]; }
                        if (reps[ii][0][1] == 0 && (i > twoTor && (i - twoTor) % 2 == 1)) { torsion *= -1; }
                        for (var j = 0; j < leng; j++) { principal *= reps[ii][1][j]; }
                        prin.push(Math.abs(principal)); tor.push(torsion);
                        if (i >= twoTor && (i - twoTor) % 2 != 0) { torsion *= -1; }
                        principal = two * two * Math.abs(principal);
                        var s = t = 0, norm = Math.sqrt(d / principal);
                        if (d == 1) { norm = 1; }
                        if (norm == parseInt(norm) && d != 1) { t = two * d; norm = parseInt(norm) * t; }
                        else {
                            norm = d * 16 / 9;
                            var ss = 1;
                            loop: while (ss <= Math.sqrt(principal * norm)) {
                                if (ss % two == 0) { var tt = 0; }
                                else { var tt = 1; }
                                var bound = Math.sqrt((principal * norm - ss * ss) / d);
                                while (tt < bound) {
                                    var tempNorm = Math.sqrt((ss * ss + tt * tt * d) / principal);
                                    if (tempNorm == parseInt(tempNorm) && (parseInt(tempNorm) * torsion - ss) % (2 * d / two) == 0) { norm = parseInt(tempNorm); s = ss; t = tt; break loop; }
                                    tt *= -1; if (tt >= 0) { tt += two; }
                                }
                                ss *= -1; if (ss > 0) { ss++; }
                            }
                        }
                        if (i >= twoTor && (i - twoTor) % 2 != 0) { s *= -1; t *= -1; }
                        dets.push([s, t]);
                    }

                    //Create window
                    var check = -1;
                    for (var i = 0; i < 3; i++) { if (document.getElementById("checkBox2," + i.toString()).innerHTML != "") { check = i; break; } }
                    if (check > 0) {
                        var path = document.createElementNS(NS, "path"), points = "M -10 -10 H " + String(maxWidth + 10) + " V " + String(maxWidth + 10) + " H -10 Z";
                        if (check == 2) {
                            points += " M " + originX.toString() + " " + originY.toString() + " h " + scale.toString() + " L ";
                            points += String(scale * (two + 1) / 2 + originX) + " " + String(originY - scale * sqrt / two) + " h " + String(-1 * scale) + " Z";
                        }
                        else { points += " M -10 " + originY.toString() + " H " + String(maxWidth + 10) + " v " + String(-1 * scale * sqrt / two) + " H -10 Z"; }
                        path.setAttributeNS(null, "d", points);
                        path.setAttributeNS(null, "fill-rule", "evenodd");
                        path.setAttributeNS(null, "fill", "#FFF");
                        path.setAttributeNS(null, "stroke", "none");
                        viewer.appendChild(path);
                    }


                    //Render
                    setTimeout(function () {
                        if (check >= 0) {
                            if (String(document.getElementById("cFrac").classList).indexOf("stayActive") > -1) { cFrac(); }
                            for (var i = total - h; i < total; i++) { render(i); }
                        }
                        setTimeout(function () {
                            document.body.classList.remove("wait"); waitWrap.classList.remove("disable");
                        }, 10);
                    }, 10);
                }, 10);

            }

            function pan(e) {
            if(1 == 0){
                ++zoomPan;
                var e = window.event || e; var check = 0;
                var x = e.clientX, y = e.clientY;
                var tempCL = canvasLeft, tempCT = canvasTop;
                canvas.addEventListener("mousemove", dragCanvas);
				document.addEventListener("mouseup", stopCanvas, true);

				function dragCanvas(e) {
				    e = window.event || e;
				    var X = x - e.clientX, Y = y - e.clientY;
				    if (Math.abs(X) > 1 || Math.abs(Y) > 1) {
				        check = 1;
				        canvasLeft = Math.min(maxWidth - canvasWidth, Math.max(0, tempCL + delta * X));
				        canvasTop = Math.min(maxWidth - canvasWidth, Math.max(0, tempCT + delta * Y));
				        canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
				    }
				}

				function stopCanvas() {
				    canvas.removeEventListener("mousemove", dragCanvas);
				    if (check == 1) { delay(zoomPan); window.event.stopPropagation(); }
				    document.removeEventListener("mouseup", stopCanvas, true);
                }

				function delay(count) {
				    setTimeout(function () {
				        if (count == zoomPan) {
					        document.body.classList.add("wait"); waitWrap.classList.add("disable");
					        setTimeout(function () {
					            if (coverings == 0) { for (var i = 0; i < total; i++) { render(i); } }
					            setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
					        }, 10);
					    }
					}, 800);
				}
				}
            }

            function zoom(e) {

				++zoomPan;
				var e = window.event || e, x = e.clientX, y = e.clientY;
                x = (x - containLeft) * delta;
                y = (y - containTop) * delta;
				if (e.type == "dblclick") { var change = 0.97; }
				else { var change = 1 - Math.max(-1, Math.min(1, (e.wheelDelta || -e.detail))) / 10; }
                var tempWidth = Math.max(0.0001 * initWidth, Math.min(canvasWidth * change, maxWidth));
                change = tempWidth / canvasWidth; canvasWidth = tempWidth; delta *= change;
                canvasLeft = Math.min(maxWidth - canvasWidth, Math.max(0, canvasLeft + (1 - change) * x));
                canvasTop = Math.min(maxWidth - canvasWidth, Math.max(0, canvasTop + (1 - change) * y));
                canvas.setAttribute("viewBox", canvasLeft.toString() + " " + canvasTop.toString() + " " + canvasWidth.toString() + " " + canvasWidth.toString());
				delay(zoomPan);
				function delay(count){
					setTimeout(function(){
					    if (count == zoomPan) {
					        document.body.classList.add("wait"); waitWrap.classList.add("disable");
					        setTimeout(function () {

                                //window
					            if (viewer.firstChild) { viewer.childNodes[0].setAttribute("stroke-width", String((0.0002 + 0.004 * styles[3][0][6]) * canvasWidth)); }

                                //selected circles
					            for (var j = 0; j < infoCount; j++) {
					                var infoStdDev = document.getElementById("infoStdDev" + j.toString());
					                if (infoStdDev) { infoStdDev.setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * infoArray[j][7]))); }
					                var newBlur = infoCircles.childNodes[2 * j];
					                var newStroke = infoCircles.childNodes[2 * j + 1], thick = 0.005 * canvasWidth * (0.05 + 3 * infoArray[j][7]);
					                newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * infoArray[j][6])));
					                if (newBlur.hasAttribute("width")) {
					                    if (parseFloat(newBlur.getAttribute("height")) < parseFloat(newBlur.getAttribute("width"))) {
					                        newBlur.setAttribute("height", thick.toString());
					                        newBlur.setAttribute("y", String(parseFloat(newStroke.getAttribute("y1")) - thick / 2));
					                    }
					                    else {
					                        newBlur.setAttribute("width", thick.toString());
					                        newBlur.setAttribute("x", String(parseFloat(newStroke.getAttribute("x1")) - thick / 2));
					                    }
					                }
					                else { newBlur.setAttribute("stroke-width", thick.toString()); }
					                var label = document.getElementById("ilabels" + j.toString());
					                if (label) {
					                    label = label.parentNode;
					                    var transform = label.getAttribute("transform"); transform = transform.split(" ");
					                    label.setAttribute("transform", transform[0] + " scale(" + String(1 * canvasWidth / initWidth) + ")");
					                }
					            }

					            if (1 == 0) {
					                for (var j = 0; j < selectCount; j++) {
					                    var selectStdDev = document.getElementById("selectStdDev" + j.toString());
					                    if (selectStdDev) { selectStdDev.setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * selectArray[j][7]))); }
					                    var newBlur = selectCircles.childNodes[2 * j];
					                    var newStroke = selectCircles.childNodes[2 * j + 1], thick = 0.005 * canvasWidth * (0.05 + 3 * selectArray[j][7]);
					                    newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * selectArray[j][6])));
					                    if (newBlur.hasAttribute("width")) {
					                        if (parseFloat(newBlur.getAttribute("height")) < parseFloat(newBlur.getAttribute("width"))) {
					                            newBlur.setAttribute("height", thick.toString());
					                            newBlur.setAttribute("y", String(parseFloat(newStroke.getAttribute("y1")) - thick / 2));
					                        }
					                        else {
					                            newBlur.setAttribute("width", thick.toString());
					                            newBlur.setAttribute("x", String(parseFloat(newStroke.getAttribute("x1")) - thick / 2));
					                        }
					                    }
					                    else { newBlur.setAttribute("stroke-width", thick.toString()); }
					                }
					            }
					            else {
					                for (var j = 0; j < selectCount; j++) {
					                    var newStroke = selectCircles.childNodes[j];
					                    if (newStroke.hasAttribute("stroke-width")) {
					                        newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * 0.18)));
					                    }
					                }
					            }

                                //labels
					            for (var j = 0; j < selectLabelCount; j++) {
					                var label = document.getElementById("labels" + j.toString()).parentNode;
					                if (label) {
					                    var transform = label.getAttribute("transform"); transform = transform.split(" ");
					                    label.setAttribute("transform", transform[0] + " scale(" + String(1 * canvasWidth / initWidth) + ")");
					                }
					            }

					            if (1 == 0) {
					                var cover = document.getElementById("cover1");
					                for (var i = cover.childNodes.length - 1; i >= 0; i--) {
					                    var element = cover.childNodes[i];
					                    if (element.hasAttribute("stroke")) {
					                        if (element.getAttribute("stroke") != "none") {
					                            element.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.15 + 3 * styles[2][0][6])));
					                        }
					                    }
					                }
					            }

                                //highlight circle
					            var i = coords[3];
					            if (i != 1000) {
					                stdDevHL.setAttribute("stdDeviation", String(canvasWidth * (0.004 + 0.003 * styles[4][i][6])));
					                for (var j = 0; j < blur.childNodes.length; j++) {
					                    var element = blur.childNodes[j];
					                    if (element.nodeType == 1) { var newBlur = element; break; }
					                }
					                for (var j = 0; j < stroke.childNodes.length; j++) {
					                    var element = stroke.childNodes[j];
					                    if (element.nodeType == 1) { var newStroke = element; break; }
					                }
					                var thick = 0.005 * canvasWidth * (0.05 + 3 * styles[4][i][6]);
					                newStroke.setAttribute("stroke-width", String(0.003 * canvasWidth * (0.1 + 3 * styles[2][i][6])));
					                if (newBlur.hasAttribute("width")) {
					                    if (parseFloat(newBlur.getAttribute("height")) < parseFloat(newBlur.getAttribute("width"))) {
					                        newBlur.setAttribute("height", thick.toString());
					                        newBlur.setAttribute("y", String(parseFloat(newStroke.getAttribute("y1")) - thick / 2));
					                    }
					                    else {
					                        newBlur.setAttribute("width", thick.toString());
					                        newBlur.setAttribute("x", String(parseFloat(newStroke.getAttribute("x1")) - thick / 2));
					                    }
					                }
					                else { newBlur.setAttribute("stroke-width", thick.toString()); }
					            }

					            //arrangement
					            if (coverings == 0) { for (var i = 0; i < total; i++) { render(i); } }

					            setTimeout(function () { document.body.classList.remove("wait"); waitWrap.classList.remove("disable"); }, 10);
					        }, 10);
					    }
					}, 500);
				}
			}



    </script>


</body>

</html>
