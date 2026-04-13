<h1>🌐 Cross-Region VPC Peering Architecture on AWS</h1>

<h2>📌 Project Overview</h2>
<p>
This project demonstrates how to connect two Virtual Private Clouds (VPCs) across different AWS regions 
(Singapore and Mumbai) using VPC Peering to enable secure private communication.
</p>

<hr>

<h2>🔹 Step 1: Create Two VPCs in Different Regions</h2>
<ul>
  <li>Created one VPC in <b>Singapore (ap-southeast-1)</b></li>
  <li>Created another VPC in <b>Mumbai (ap-south-1)</b></li>
  <li>Used non-overlapping CIDR blocks:</li>
  <ul>
    <li>VPC 1: 10.0.0.0/16</li>
    <li>VPC 2: 192.168.0.0/16</li>
  </ul>
</ul>

<hr>

<h2>🔹 Step 2: Configure Subnets, Route Tables & Internet Gateway</h2>
<ul>
  <li>Created subnets inside each VPC (e.g., 10.0.1.0/24)</li>
  <li>Attached Internet Gateway to each VPC</li>
  <li>Configured route tables:</li>
  <pre>0.0.0.0/0 → Internet Gateway</pre>
</ul>

<hr>

<h2>🔹 Step 3: Launch EC2 Instances</h2>
<ul>
  <li>Launched EC2 instance in Singapore VPC</li>
  <li>Launched EC2 instance in Mumbai VPC</li>
  <li>Each instance has:
    <ul>
      <li>Private IP (for internal communication)</li>
      <li>Public IP (for remote access)</li>
    </ul>
  </li>
</ul>

<hr>

<h2>🔹 Step 4: Create VPC Peering Connection</h2>
<ul>
  <li>Initiated peering request from Singapore VPC</li>
  <li>Accepted request in Mumbai region</li>
  <li>Established cross-region VPC peering connection</li>
</ul>

<hr>

<h2>🔹 Step 5: Update Route Tables</h2>
<p><b>Singapore VPC Route Table:</b></p>
<pre>192.168.0.0/16 → VPC Peering Connection</pre>

<p><b>Mumbai VPC Route Table:</b></p>
<pre>10.0.0.0/16 → VPC Peering Connection</pre>

<hr>

<h2>🔹 Step 6: Configure Security Groups</h2>
<ul>
  <li>Allowed ICMP (ping) traffic</li>
  <li>Added inbound rules for peer VPC CIDR</li>
</ul>

<pre>
Type: All ICMP
Source: 192.168.0.0/16
</pre>

<hr>

<h2>🔹 Step 8: Test Connectivity</h2>
<pre>ping &lt;private-ip-of-other-EC2&gt;</pre>

<ul>
  <li>Verified successful communication using private IP</li>
</ul>

<hr>

<h2>🚧 Challenges Faced</h2>
<ul>
  <li>Missing route table entries</li>
  <li>Security group blocking ICMP</li>
</ul>

<hr>

<h2>✅ Final Result</h2>
<p>
Successfully achieved private communication between EC2 instances across regions 
without using the public internet.
</p>

<hr>

<h2>💡 Skills Demonstrated</h2>
<ul>
  <li>Cloud Networking</li>
  <li>AWS VPC</li>
  <li>EC2</li>
  <li>Routing</li>
  <li>Security Groups</li>
  <li>Troubleshooting</li>
</ul>
