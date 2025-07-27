---
title: "Introduction to Bayesian Data Analysis"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/2014-spring-teaching-1
date: 27-07-2025
location: "Kolkata, India"
---

This is a description of a teaching experience. You can use markdown like any other post.

Why Bayesian at All?
======
Statistics as a subject has not been around for a long time. It had started to materialise as a discipline when gamblers realised they could mathematically quantify "chance" which facilitated their study of gains and losses. Now how we define "chance" is what leads us to the 2 schools of thought in Statistics.

<h3>The Frequentist Version</h3>

Toss a coin 100 times. Count the proportion of heads among the 100 trials. Here's a simple code to run this:

<textarea id="rcode" rows="12" cols="70">
set.seed(1)

heads <- sample(c(0, 1), size = 100, rep = TRUE)

proportion_heads <- cumsum(heads) / (1:100)

plot(1:100, proportion_heads,
     xlab = "No of Trials",
     ylab = "Proportion of Heads",
     main = "Cumulative Proportion of Heads (Fair Coin Toss)",
     ylim = c(0, 1),
     type = "b")

abline(h = 0.5, col = "red", lty = 2)
</textarea>
<br>
<button onclick="runR()">Run R Code</button>

<pre id="r-output">Text output will appear here...</pre>
<canvas id="r-plot" width="600" height="400" style="border:1px solid #ccc; margin-top:10px;"></canvas>

<script type="module">
  import * as webR from 'https://webr.r-wasm.org/latest/webr.mjs';
  const webr = new webR.WebR();
  await webr.init();

  window.runR = async () => {
    const code = document.getElementById("rcode").value;

    // Clear previous output
    document.getElementById("r-output").innerText = "";
    const canvas = document.getElementById("r-plot");
    const ctx = canvas.getContext("2d");
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Open graphics device
    await webr.evalRVoid(`
      library(grDevices)
      png("plot.png", width=600, height=400)
    `);

    // Run the R code
    const result = await webr.evalR(code);
    const output = await result.toArray();
    document.getElementById("r-output").innerText = output.join("\n");

    // Close the device and get image
    await webr.evalRVoid("dev.off()");
    const plot = await webr.FS.readFile("plot.png", { encoding: "binary" });
    const blob = new Blob([plot], { type: "image/png" });
    const url = URL.createObjectURL(blob);
    const img = new Image();
    img.onload = () => {
      ctx.drawImage(img, 0, 0);
      URL.revokeObjectURL(url);
    };
    img.src = url;
  };
</script>

<style>
  textarea#rcode {
    width: 90%;
    font-family: 'Fira Code', monospace;
    font-size: 14px;
    padding: 10px;
    border: 2px solid #444;
    border-radius: 10px;
    background-color: #f3f3f3;
    color: #222;
    box-shadow: 2px 2px 5px rgba(0,0,0,0.1);
  }

  button {
    margin-top: 10px;
    padding: 8px 16px;
    font-size: 14px;
    font-weight: bold;
    background-color: #0057b7;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0041a3;
  }

  pre#r-output {
    margin-top: 15px;
    background-color: #111;
    color: #0f0;
    padding: 10px;
    border-radius: 8px;
    font-family: 'Courier New', Courier, monospace;
    white-space: pre-wrap;
    word-wrap: break-word;
  }

  canvas#r-plot {
    margin-top: 10px;
    border-radius: 8px;
    background-color: #fff;
  }
</style>


Heading 2
======

Heading 3
======
