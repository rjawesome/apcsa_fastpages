---
layout: page
title: Mean
permalink: /mean/
---

# Mean Calculator

<div id="page">
<div id="calc">
<div id="items">
</div>
<button id="add-new">Add new</button>
<p id="mean">Mean: </p>
</div>
</div>

<script>
var curItems = 0;
var itemsDiv = document.getElementById("items");
var meanElem = document.getElementById("mean");
var itemsArr = [];

function recalculateMean () {
  var sum = 0;
  var items = 0;
  for (var i = 0; i<curItems; i++) {
    if (!isNaN(itemsArr[i])) {
      sum += itemsArr[i];
      items++;
    }
  }
  if (items > 0) {
    var mean = sum/items;
    meanElem.innerHTML = "Mean: " + mean.toString();
  } else {
    meanElem.innerHTML = "Mean: ";
  }
}

document.getElementById("add-new").onclick = function () {
  itemsArr.push(NaN);
  var theCurrentItem = curItems;

  var newInput = document.createElement("input");
  newInput.type = "text";
  newInput.placeholder = "Item #" + (curItems+1).toString();
  newInput.id = "item"+curItems;
  newInput.onkeyup = function () {
    itemsArr[theCurrentItem] = parseFloat(newInput.value);
    if (!isNaN(itemsArr[theCurrentItem])) {
      newInput.classList.add("valid");
    } else {
      newInput.classList.remove("valid");
    }
    recalculateMean();
  }

  itemsDiv.appendChild(newInput);
  curItems++;
}
</script>

<style>
input[type="text"] {
	display: block;
  margin-bottom: 10px;
  padding: 5px;
  border: 2px solid red;
  border-radius: 4px;
}
input[type="text"].valid {
  border: 2px solid green;
}
#page {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>