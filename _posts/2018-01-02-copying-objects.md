---
keywords: fastai
title: Copying objects in Python
nb_path: _notebooks/2018-01-02-copying-objects.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2018-01-02-copying-objects.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this tutorial we compare a shallow versus deep copy in Python using the inbuilt <code>copy</code> module.</p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">copy</span> <span class="kn">import</span> <span class="n">copy</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="1.-Assignment">1. Assignment<a class="anchor-link" href="#1.-Assignment"> </a></h2><p>First we create a list called foo_list which has three items: two ints and one list of ints. We run the in-built <code>id</code> function to check the address of the list object in memory.</p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">]]</span>

<span class="c1"># check the item&#39;s address in memory</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>2930710693248</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Next we create a second variable called foo_list_two which is assigned to foo_list. We can see that both variables point to the same object in memory.</p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list_two</span> <span class="o">=</span> <span class="n">foo_list</span>

<span class="c1"># Check the two variables point to the same object</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span> <span class="o">==</span> <span class="nb">id</span><span class="p">(</span><span class="n">foo_list_two</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>True</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">11</span>

<span class="c1"># Check the second list</span>
<span class="n">foo_list_two</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>[11, 2, [3, 4]]</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">%</span><span class="k">reset</span> -f
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.-Shallow-copy">3. Shallow copy<a class="anchor-link" href="#3.-Shallow-copy"> </a></h2>
</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">]]</span>

<span class="c1"># check the item&#39;s address in memory</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>2930709728704</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list_two</span> <span class="o">=</span> <span class="n">foo_list</span><span class="o">.</span><span class="n">copy</span><span class="p">()</span>

<span class="c1"># Check the two variables point to the same object</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span> <span class="o">==</span> <span class="nb">id</span><span class="p">(</span><span class="n">foo_list_two</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>False</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span><span class="p">[</span><span class="mi">2</span><span class="p">][</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">11</span>

<span class="c1"># Check the second list</span>
<span class="n">foo_list_two</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>[1, 2, [11, 4]]</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="3.-Deep-copy">3. Deep copy<a class="anchor-link" href="#3.-Deep-copy"> </a></h2><p>A deep copy creates a new object and recursively adds the copies of nested objects present in the original elements.</p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">copy</span> <span class="kn">import</span> <span class="n">deepcopy</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">]]</span>

<span class="c1"># check the item&#39;s address in memory</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>2930709811328</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list_two</span> <span class="o">=</span> <span class="n">deepcopy</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>

<span class="c1"># Check the two variables point to different objects</span>
<span class="nb">id</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span> <span class="o">==</span> <span class="nb">id</span><span class="p">(</span><span class="n">foo_list_two</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">



<div class="output_text output_subarea output_execute_result">
<pre>False</pre>
</div>

</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span><span class="p">[</span><span class="mi">2</span><span class="p">][</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">11</span>

<span class="c1"># Check that the deep copied list does not update</span>
<span class="nb">print</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">foo_list_two</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>[11, 2, [11, 4]]
[1, 2, [3, 4]]
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">foo_list</span><span class="p">[</span><span class="mi">2</span><span class="p">][</span><span class="mi">0</span><span class="p">]</span> <span class="o">=</span> <span class="mi">22</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="n">foo_list</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">foo_list_two</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>[11, 2, [22, 4]]
[1, 2, [3, 4]]
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

</div>
 
