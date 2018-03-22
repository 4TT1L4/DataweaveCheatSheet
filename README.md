# Dataweave Cheatsheet

<table>
<tr>
<th colspan=3>

__XML attribute in output__

<tr>
<th>
Input
<th>
Transformation
<th>
Output
<tr>
<td>
  
~~~~
[{
	"ID": 1,
	"code": "ER38sd",
	"destination": "SFO",
	"plane": {
		"type": "Boeing 737",
		"totalSeats": 150
	}
}, {
	"ID": 2,
	"code": "ER45if",
	"destination": "LAX",
	"plane": {
		"type": "Boeing 777",
		"totalSeats": 300
	}
}]
~~~~

<td>
  
~~~~
%dw 1.0
%output application/xml
---
flights: {(payload map {
	flight @(flightCode: $.code):
	{	
		destination: $.destination
	}
 })
}
~~~~
  
<td>
  
  
~~~~
<?xml version='1.0' encoding='windows-1252'?>
<flights>
  <flight flightCode="ER38sd">
    <destination>SFO</destination>
  </flight>
  <flight flightCode="ER45if">
    <destination>LAX</destination>
  </flight>
</flights>
~~~~
  
  
</table>
