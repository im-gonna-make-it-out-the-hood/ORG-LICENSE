// ==UserScript==
// @name        blame @split@coolviruses.download for this one - github.com
// @namespace   Violentmonkey Scripts
// @match       https://github.com/*/LICENSE*
// @grant       none
// @version     1.0
// @run-at      document-idle
// @author      -
// @description 9/28/2023, 8:20:36 PM
// ==/UserScript==
let theBox = document.querySelector(".Box-sc-g0xbh4-0 .clRvgz");
let theOtherBox = document.querySelector(".Box-sc-g0xbh4-0 .kUXbOh");
let license = null;

let id = setInterval(() => {
  if ((theBox === null) | (theOtherBox === null)) {
    theBox = document.querySelector(".Box-sc-g0xbh4-0 .clRvgz");
    theOtherBox = document.querySelector(".Box-sc-g0xbh4-0 .kUXbOh");
  } else {
    clearInterval(id);
    license = theBox.children[1].innerHTML;
    theBox.children[0].innerHTML = "Hi, I'm Saul Goodman.";
    theBox.children[1].innerHTML = "Did you know that you have rights?";

    const previousContent = theOtherBox.innerHTML;
    theOtherBox.innerHTML = `${license.startsWith("The") ? "" : "The"} <strong>${license}</strong> says you do. ${previousContent}`;
  }
}, 100);
