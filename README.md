# aws_s3_consolidate - Full Report

## Introduction

In this project will be looking at:
  1. Build a robust data pipeline capable of processing large amount of data
  2. Within this pipeline:
  1. Consolidate the various data sources
  2. Clean the data
  3. Extract relevant features for the modelling job

## Data & Tools Description

### Data:
<pre>
The data set contains 4 files:
  1- “vibration_axis_A_axis_B.csv”
  2- “vibration_axis_C.csv”
  3- “vibration_axis_D.csv” contains data vibration sensors captured at various frequencies.
  4- “milling_modes.csv” describes the start date of each operating mode of the milling machine.
  </pre>
  
### Tools:
<pre>
For this project, i used some AWS components : 
  1- S3 to store my data
  2- AWS EMR to run Spark cluster with jupyter notebook activated to work with data in S3
  </pre>
  
 ### Language: Python with Pyspark  

## Methodology

### 1- Business Understanding

First of all, in this project i have used my own AWS environment to transfrorm my data i had a storage limit of <b>6 GB</b>.
The total size of files in csv is : <b>7.67 GB</b>.
So i have to compress my files to another format to fit the space limit in AWS S3.

This is a comparision between file format used by Spark :
![alt text](https://github.com/MourabitElBachir/aws_s3_consolidate/blob/main/ORC_PARQUET.JPG)

#### As you have seen the ORC format is what we need for compression & it will help us to optimise reading anytime we use the files in our program (reading one time csv file to transform files in orc format & after use orc format as main format of reading is very efficient than reading csv each time)

### 2- Analytic Approach

In this project i decided to remove rows with null values & to delete rows with wrong date format 

### 4- Data Collection & Understanding

Input data : will be in orc format
Output data : will be in orc format for forecasting & in this repository i uploded my consolidation(output) data in csv format to see results

## Results

This is the result i got after running my two programs :

<div class="row"><div class="col-md-12"><div class="panel panel-success"><div class="panel-heading "><h3 class="panel-title">HTML Table Preview</h3></div>
<table border=1 class="table table-striped table-bordered table-hover table-condensed">
<thead><tr><th title="Field #1">date_AB</th>
<th title="Field #2">value_A</th>
<th title="Field #3">value_B</th>
<th title="Field #4">date_D</th>
<th title="Field #5">value_D</th>
<th title="Field #6">date_C</th>
<th title="Field #7">value_C</th>
<th title="Field #8">debut_prog_mode</th>
<th title="Field #9">programme</th>
<th title="Field #10">mode</th>
</tr></thead>
<tbody><tr><td>2018-12-29 16:06:40.000000</td>
<td align="right">0.13627758136417167</td>
<td align="right">-0.46486274253922771</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000050</td>
<td align="right">-0.21216823394973788</td>
<td align="right">-0.38960961433052582</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000100</td>
<td align="right">0.65112665400009972</td>
<td align="right">-0.09225297692872193</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000150</td>
<td align="right">0.04519463605601759</td>
<td align="right">-0.31353998453994975</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000200</td>
<td align="right">0.97396150810693660</td>
<td align="right">-0.47329137618961342</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000250</td>
<td align="right">1.12212019229080262</td>
<td align="right">-0.49637203205715824</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000300</td>
<td align="right">0.94635881896509466</td>
<td align="right">-0.27892631100541726</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000350</td>
<td align="right">-0.12323909305050784</td>
<td align="right">-0.49473257271133458</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000400</td>
<td align="right">0.04028634421692867</td>
<td align="right">-0.37565097239413631</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000450</td>
<td align="right">0.44116687802921162</td>
<td align="right">-0.32223175544471550</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000500</td>
<td align="right">1.16733105031942586</td>
<td align="right">-0.55981545957599887</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000550</td>
<td align="right">-0.07146106778474581</td>
<td align="right">-0.61952093498810579</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000600</td>
<td align="right">1.17784308586246844</td>
<td align="right">-0.49356270395862251</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000650</td>
<td align="right">1.13402618492376295</td>
<td align="right">-0.63083753243630669</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000700</td>
<td align="right">1.55918992438873616</td>
<td align="right">-0.19854665795461832</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000750</td>
<td align="right">1.77103927893121060</td>
<td align="right">-0.71211490193560512</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000800</td>
<td align="right">1.94704577062063344</td>
<td align="right">-0.64207180459013757</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000850</td>
<td align="right">1.43466099097175181</td>
<td align="right">-0.28560272179678475</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000900</td>
<td align="right">0.43177779962366492</td>
<td align="right">-0.70576421679912116</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.000950</td>
<td align="right">0.77846054742392035</td>
<td align="right">-0.57559621060520805</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001000</td>
<td align="right">1.85177470855271897</td>
<td align="right">-0.54950479752506587</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001050</td>
<td align="right">1.09106776580024545</td>
<td align="right">-0.31910672528193168</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001100</td>
<td align="right">1.64620958845893073</td>
<td align="right">-0.35797110747968497</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001150</td>
<td align="right">1.24414928700433469</td>
<td align="right">-0.30751015241083213</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001200</td>
<td align="right">1.00514985594978290</td>
<td align="right">-0.08610960890964826</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
<tr><td>2018-12-29 16:06:40.001250</td>
<td align="right">1.07977384386285191</td>
<td align="right">-0.59288032843410121</td>
<td>2018-12-29 16:06:40</td>
<td align="right">-9.613326548667038</td>
<td>2018-12-29 16:06:40</td>
<td align="right">1.0556886269138857</td>
<td>2018-12-29 16:06:40</td>
<td>prg3</td>
<td>mode3</td>
</tr>
</tbody></table>
</div></div></div>
