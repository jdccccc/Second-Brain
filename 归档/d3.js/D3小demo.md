---
title: D3小demo
date: 2021-05-11 16:08:04
tags: d3
---

# 可增加条数的条形图

```
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <title>朴素贝叶斯演示</title>
    <link rel="stylesheet" href="./style.css" />
    <script src="D:/d3/d3.js"></script>
</head>

<body>
    <script type="text/javascript">
        var w = 600,
            h = 250,
            dataset = [],
            dataNum = 10,
            padding = 40;

        for (let i = 0; i < dataNum; i++) {
            let x = Math.floor(Math.random() * 25) + 4;
            dataset.push(x);
        }

        var xScale = d3.scaleBand()
            .domain(d3.range(dataset.length))
            .range([padding, w]);

        var yScale = d3.scaleLinear()
            .domain([0, d3.max(dataset)])
            .range([h - padding, padding]);
        var svg = d3.select("body")
            .append("svg")
            .attr("width", w)
            .attr("height", h);

        var rect = svg.selectAll("rect")
            .data(dataset)
            .enter()
            .append("rect")
            .attr("x", function(d, i) {
                return xScale(i);
                //动态实现横向平均排列
            })
            .attr("y", function(d) {
                return yScale(d);
            })
            .attr("width", 0.95 * (xScale(1) - padding))
            .attr("height", function(d) {
                return h - padding - yScale(d);
            })
            .attr("fill", function(d) {
                return "rgb(0," + 8 * d + "," + 7 * d + ")";
                //数字与字符串相加变成数字字符
            });
        var text = svg.selectAll("text")
            .data(dataset)
            .enter()
            .append("text")
            .text(function(d) {
                return d;
            })
            .attr("x", function(d, i) {
                return xScale(i) + 0.5 * (xScale(1) - padding) - 1;
            })
            .attr("y", function(d) {
                return yScale(d) + 15;
            })
            .attr("font-family", "sans-serif")
            .attr("font-size", "11px")
            .attr("fill", "white")
            .attr("text-anchor", "middle");

        var xAxis = d3.axisBottom(xScale);
        var yAxis = d3.axisLeft(yScale).ticks(6);


        svg.append("g")
            .attr("transform", "translate(0," + (h - padding) + ")")
            .call(xAxis)
            .attr("class", "axis");


        svg.append("g")
            .attr("transform", "translate(" + (padding) + ",0)")
            .call(yAxis)
            .attr("class", "axis");
    </script>

    <p id="p1">Click on this text to update the chart with new data values (once).</p>
    <script type="text/javascript">
        d3.select("#p1")
            .on("click", function() {
                svg.selectAll("g").remove();
                //更新时一定要删除数轴重新创建，否则text将会无法正确显示
                // var dataset = [],
                var t = 100,
                    maxNum = 25;
                var newNum = Math.floor(Math.random() * maxNum) + 4;
                dataset.push(newNum);

                // for (let i = 0; i < dataNum; i++) {
                //     let x = Math.round(Math.random() * maxNum + 4);
                //     dataset.push(x);
                // }
                var xScale = d3.scaleBand()
                    .domain(d3.range(dataset.length))
                    .range([padding, w]);

                var yScale = d3.scaleLinear()
                    .domain([0, d3.max(dataset)])
                    .range([h - padding, padding]);

                var bars = svg.selectAll("rect")
                    .data(dataset);

                bars.enter()
                    .append("rect")
                    .attr("x", w)
                    .attr("y", function(d) {
                        return yScale(d);
                    })
                    .attr("width", xScale(1) - padding)
                    .attr("height", function(d) {
                        return h - padding - yScale(d);
                    })
                    .attr("fill", function(d) {
                        return "rgb(0," + 8 * d + "," + 7 * d + ")";
                    });



                svg.selectAll("text")
                    .data(dataset)
                    .enter()
                    .append("text")
                    .text(function(d) {
                        return d;
                    })
                    .attr("x", w + (xScale(1) - padding) / 2)
                    .attr("y", function(d) {
                        return yScale(d) + 15;
                    })
                    .attr("font-family", "sans-serif")
                    .attr("font-size", "11px")
                    .attr("fill", "white")
                    .attr("text-anchor", "middle");


                svg.selectAll("rect")
                    .transition()
                    .delay(function(d, i) {
                        return i * t;
                    })
                    .duration(1000)
                    .attr("x", function(d, i) {
                        return xScale(i);
                    })
                    .attr("y", function(d) {
                        return yScale(d);
                    })
                    .attr("width", 0.95 * (xScale(1) - padding))
                    .attr("height", function(d) {
                        return h - padding - yScale(d);
                    })
                    .attr("fill", function(d) {
                        return "rgb(0," + 8 * d + "," + 7 * d + ")";
                    });

                svg.selectAll("text")
                    .transition()
                    .delay(function(d, i) {
                        return i * t;
                    })
                    .duration(1000)
                    .text(function(d) {
                        return d;
                    })
                    .attr("x", function(d, i) {

                        return xScale(i) + 0.5 * (xScale(1) - padding) - 1;
                    })
                    .attr("y", function(d) {
                        return yScale(d) + 15;
                    });
                //动画转换方式多种多样
                var xAxis = d3.axisBottom(xScale);
                var yAxis = d3.axisLeft(yScale).ticks(6);
                svg.append("g")
                    .transition()
                    .duration(2000)
                    .attr("transform", "translate(0," + (h - padding) + ")")
                    .call(xAxis)
                    .attr("class", "axis");
                svg.append("g")
                    .transition()
                    .duration(2000)
                    .attr("transform", "translate(" + (padding) + ",0)")
                    .call(yAxis)
                    .attr("class", "axis");
            })
    </script>

    <p id="p2">Click on this text to remove a data value from the chart!</p>
    <script>
        d3.select("#p2")
            .on("click", function() {
                // svg.select("g").remove();
                dataset.shift();
                svg.selectAll("rect")
                    .data(dataset)
                    .exit()
                    .transition()
                    .duration(500)
                    .attr("x", w)
                    .remove()
                svg.selectAll("text")
                    .data(dataset)
                    .exit()
                    .transition()
                    .duration(500)
                    .attr("x", w)
                    .remove()
            })
    </script>
</body>

</html>
```

