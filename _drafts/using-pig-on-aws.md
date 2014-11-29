---
layout: post
title:  "Using Pig on AWS"
date:   2014-08-01
categories: random
---

<h2>UW Data Science Course on Coursera</h2>

<p>Setting up a Pig cluster</p>

<ol>
	<li>set up an AWS account and create a new access key</li>
	<li>create an ssh key pair for Amazon EC2</li>
		<ul>
			<li>'chmod 600 key-pair.pem' makes the key only usable by you
		</ul>
	<li>Create cluster</li>
		<ul>
			<li>Name the cluster</li>
			<li>Uncheck logging</li>
			<li>Under Software Configuration, we used AMI Version 2.4.2</li>
			<li>Under Security and Access, select the Key Pair</li>
			<li>Create Cluster</li>
		</ul>
	<li>ssh -o "ServerAliveInterval 10" -i </path/to/saved/keypair/file.pem> hadoop@<master.public-dns-name.amazonaws.com> </li>
	<li>type 'yes' when prompted</li>
	<li>type 'pig' to enter the interactive Pig console [grunt>]</li>
</ol>

<p>Monitoring Hadoop jobs -- ssh tunneling</p>
<ol>
	<li>ssh -L 9100:localhost:9100 -L 9101:localhost:9101  -i </path/to/saved/keypair/file.pem> hadoop@<master.public-dns-name.amazonaws.com></li>
	<li>go to: http://localhost:9101/</li>
	<li></li>
</ol>

<p>Kill a Hadoop job</p>
<ol>
	<li>first kill pig using Ctrl + C</li>
	<li>then kill the Hadoop job using: '% hadoop job -kill job_id' with the job_id coming from the ob tracker interface</li>
	<li></li>
</ol>

<p>Terminating an AWS Cluster</p>
<ol>
	<li>From the management console, select the job and click Terminate</li>
	<li>Wait until the job reads TERMINATED</li>
	<li></li>
</ol>

<p>Copy from AWS</p>
<ol>
	<li>to copy from the HDFS to the master node<pre>fs -getmerge  /user/hadoop/example-results example-results</pre></li>
	<li>to copy an entire directory recursively from the master node to local file system <pre>scp -o "ServerAliveInterval 10" -i </path/to/saved/keypair/file.pem> -r hadoop@<master.public-dns-name.amazonaws.com>:example-results .</pre></li>
	<li></li>
</ol>

<p>Run pig locally</p>
<ol>
	<li>'pig -x local' instead of 'pig'</li>
	<li>'store count_by_counts_ordered into '/tmp/finaloutput' using PigStorage();'</li>
</ol>
