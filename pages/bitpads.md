---
layout: page
title: Bitpads
permalink: /bitpads/
---

<div class="home-columns">
  <div class="column-left">
<div class="home">
<h2></h2>
<p>Bitpads are designed to serve individuals or entities, such as businesses, in their fundamental capacities as observers, organizers, traders and supporters of innumerable kinds of processes.</p>
<p>The primary purpose of Bitpads Protocol is to support the indefinite reliability of transmitting signals and messages using numerous and unforseeable mediums, and in steady or hostile circumstances.</p>
<hr>
<br>
<p>Every bitpad begins with the same set of 8 flags, ensuring that initial transmission can be contained within a standard byte (8-bit) sequence which UART/serial systems require.</p>

<h3>Initial Flags</h3>
<p>The first 4 flags that initiate a bitpad transmission are:</p>
<ol>
  <li><strong>Wave or Record?</strong> Off or On</li>
  <li><strong>Pad</strong> Off or On</li>
  <li><strong>Record Flags</strong> Off or On</li>
  <li><strong>Message</strong></li>
  <li><strong>Task</strong></li>
  <li><strong>Time</strong></li>
  <li><strong>Note</strong></li>
  <li><strong>Count</strong></li>
</ol>

<hr>

<h3>What is a Wave?</h3>
<p>
  A <strong>"Wave"</strong> is the simplest, rawest form of purposeful transmission. Waves consist only of flag sequences. 
  Waves communicate instructions from one device to another using:
</p>
<ul>
  <li>Individual True or False flags</li>
  <li>Alternating sets of bits</li>
  <li>Or a combination of the two</li>
</ul>

<p>The ordering of flags is achieved in 3 main ways:</p>
<ol>
  <li><strong>Hard-coded</strong> between two devices via a controlling system</li>
  <li><strong>Setup Signal</strong> via the preceding transmission</li>
  <li><strong>Wave Sequence</strong> via the subsequent transmission</li>
</ol>

<hr>

<h3>Pad and Record Interpretation</h3>
<ul>
  <li>The <strong>2nd flag</strong> confirms if the Record is to be treated as a full Bitpad with the powers and permissions which its controlling system may provide.</li>
  <li>If <strong>Flag 1 is On</strong> and <strong>Flag 2 is Off</strong>, the transmission is treated as a plain record (equivalent to a log).</li>
  <li>If <strong>Flags 1 and 2 are On</strong>, but <strong>Flag 3 is Off</strong> ("No Record Flags"), then bits 5–8 are set to Off and the Bitpad prepares to read all remaining content from just the <strong>Message Sequence</strong>.</li>
  <li>If <strong>Flags 1, 2, and 3 are On</strong>, then bits 5–8 are optionally set to On or Off as the particular Bitpad requires, and the device prepares to read those sequences in turn.</li>
</ul>

<hr>

<h3>Special Case: Message in Waves</h3>
<ul>
  <li><strong>Flag 4 ("Message")</strong> can be set to On or Off for a Wave.</li>
  <li>It <strong>may be set to Off when Flag 1 is On and Flag 2 is Off</strong>, but <strong>only when Flag 3 is On</strong>.</li>
</ul>

<hr>


</div>
</div>


 <div class="column-right">
<h3>Updates</h3>
<ul>
    <li>
      <a href="categories/bitpads/">Bitpads</a></li>
    <li>
      <a href="https://x.com/bitpadsproject">Posts on X</a></li>
</ul>

<h3>Sites</h3>
<ul>
    <li>
      <a href="https://github.com/babbworks/bitpads">GitHub</a></li>
    <li>
      <a href="https://workwarrior.org">bitpads.org</a></li>
</ul>
<h3>Project</h3>
<ul>
    <li>
      <a href="https://github.com/babbworks/bitpads/blob/master/readme.md">Readme</a></li>
</ul>
  </div>
</div>