---


---

<hr>
<h2 id="layout-posttitle-pagination-postauthor-chester">layout: post<br>
title: “Pagination Post”<br>
author: “Chester”</h2>
<h4 id="question">Question:</h4>
<blockquote>
<p>Given an array  <code>A</code>  of integers, return the  <strong>length</strong>  of the longest arithmetic subsequence in  <code>A</code>.</p>
</blockquote>
<p>Recall that a  <em>subsequence</em>  of  <code>A</code>  is a list  <code>A[i_1], A[i_2], ..., A[i_k]</code>  with  <code>0 &lt;= i_1 &lt; i_2 &lt; ... &lt; i_k &lt;= A.length - 1</code>, and that a sequence  <code>B</code> is  <em>arithmetic</em>  if  <code>B[i+1] - B[i]</code>  are all the same value (for  <code>0 &lt;= i &lt; B.length - 1</code>).</p>
<p><strong>Examples:</strong></p>
<blockquote>
<p><strong>Input:</strong> [3,6,9,12]<br>
<strong>Output:</strong> 4<br>
<strong>Explanation:</strong><br>
The whole array is an arithmetic sequence with steps of length = 3.</p>
</blockquote>
<blockquote>
<p><strong>Input:</strong> [9,4,7,2,10]<br>
<strong>Output:</strong> 3<br>
<strong>Explanation:</strong><br>
The longest arithmetic subsequence is [4,7,10].</p>
</blockquote>
<blockquote>
<p><strong>Input:</strong> [20,1,15,3,10,5,8]<br>
<strong>Output:</strong> 4<br>
<strong>Explanation:</strong><br>
The longest arithmetic subsequence is [20,15,10,5].</p>
</blockquote>
<p>Note:</p>
<ol>
<li><code>2 &lt;= A.length &lt;= 2000</code></li>
<li><code>0 &lt;= A[i] &lt;= 10000</code></li>
</ol>
<h4 id="solution">Solution:</h4>

