<h1>Deployments</h1>
<p>The following are application deployments from the IS Development team.  This list is maintained and should be considered the authoritative documentation for all IS Development related applications.</p>

<h2 id="COFASV30">COFASV30</h2>
<p>The primary duty of this host is to serve Express applications utilized as the backend for most applications built by the IS Development team.  This server is behind the network firewall and is reached by public internet via proxy from COFASV32.  All Express applications are managed using PM2 daemon process manager that are accessed by dedicated port via Nginx reverse proxy.</p>

<h3>Apps</h3>
<table>
  <tr>
    <th>Name</th>
    <th>URL</th>
    <th>PORT</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Department Purchasing API</td>
    <td><a href="https://api.franklin-gov.com/api/v2/dept-purchasing" target="_blank">https://api.franklin-gov.com/api/v2/dept-purchasing</a></td>
    <td>5000</td>
    <td>Handles database functionality for department purchasing application.</td>
  </tr>
  <tr>
    <td>Revenue Management Tools API</td>
    <td><a href="https://api.franklin-gov.com/rev-mgmt-tools" target="_blank">https://api.franklin-gov.com/rev-mgmt-tools</a></td>
    <td>5001</td>
    <td>Revenue Management Tools backend.</td>
  </tr>
  <tr>
    <td>Indect Parking API</td>
    <td><a href="https://api.franklin-gov.com/indect/structure" target="_blank">https://api.franklin-gov.com/indect/structure</a></td>
    <td>5002</td>
    <td>Proxies requests to the Indect API for the parking garage availability application.</td>
  </tr>
  <tr>
    <td>FFD API</td>
    <td><a href="https://api.franklin-gov.com/api/v1/ffd" target="_blank">https://api.franklin-gov.com/api/v1/ffd</a></td>
    <td>5003</td>
    <td>Backend for multiple FFD related applications.</td>
  </tr>
  <tr>
    <td>Engineering API</td>
    <td><a href="https://api.franklin-gov.com/api/v1/eng" target="_blank">https://api.franklin-gov.com/api/v1/eng</a></td>
    <td>5004</td>
    <td>Backend for multiple Engineering and Planning related applications.</td>
  </tr>
  <tr>
    <td>PD API</td>
    <td><a href="https://api.franklin-gov.com/api/v1/pd" target="_blank">https://api.franklin-gov.com/api/v1/pd</a></td>
    <td>5005</td>
    <td>Backend for multiple PD related applications.</td>
  </tr>
  <tr>
    <td>Ubuntu Cockpit</td>
    <td><a href="http://cofasv30:9090/system" target="_blank">http://cofasv30:9090/system</a></td>
    <td>9090</td>
    <td>Ubuntu Cockpit utilty for managing Linux servers via browser.</td>
  </tr>
</table>

<h2 id="COFASV32">COFASV32</h2>
<p>DMZ Linux web server hosts frontend applications that are primarily used for internal business processes only and do not have a public facing element.  Also acts as a proxy for all public internet traffic on COFASV30 by way of Nginx.</p>

<h3>Apps</h3>
<table>
  <tr>
    <th>Name</th>
    <th>URL</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Stormwater Site Innspections</td>
    <td><a href="https://dev.franklintn.gov/stormwater" target="_blank">https://dev.franklintn.gov/stormwater</a></td>
    <td>Utilized by the Engineering Department to track site inspections and violations.</td>
  </tr>
  <tr>
    <td>Department Purchasing</td>
    <td><a href="https://dev.franklintn.gov/dept-purchasing" target="_blank">https://dev.franklintn.gov/dept-purchasing</a></td>
    <td>Currently in use by Fire and Parks departments - allows for submission and tracking of purchases and purchase requests.</td>
  </tr>
  <tr>
    <td>CIP Tracker</td>
    <td><a href="https://dev.franklintn.gov/cip" target="_blank">https://dev.franklintn.gov/cip</a></td>
    <td>Application used to track the lifecycle of capital investment projects.  Has a public facing element hosted on COFASV03.</td>
  </tr>
  <tr>
    <td>Crime Scene Stats</td>
    <td><a href="https://dev.franklintn.gov/crime-scene" target="_blank">https://dev.franklintn.gov/crime-scene</a></td>
    <td>PD application used by crime scene technicians to track processes and materials used for case work.</td>
  </tr>
  <tr>
    <td>Project Vesting</td>
    <td><a href="https://dev.franklintn.gov/vesting" target="_blank">https://dev.franklintn.gov/vesting</a></td>
    <td>Planning Department application tracks project vesting lifecycles.</td>
  </tr>
  <tr>
    <td>PD API <em>Proxy</em></td>
    <td><a href="https://dev.franklintn.gov/api/v1/pd" target="_blank">https://dev.franklintn.gov/api/v1/pd</a></td>
    <td>Proxy for <a href="https://api.franklintn-gov.com/api/v1/pd" target="_blank">https://api.franklintn-gov.com/api/v1/pd</a></td>
  </tr>
  <tr>
    <td>Department Purchasing API <em>Proxy</em></td>
    <td><a href="https://dev.franklintn.gov/api/v2/dept-purchasing" target="_blank">https://dev.franklintn.gov/api/v2/dept-purchasing</a></td>
    <td>Proxy for <a href="https://api.franklintn-gov.com/api/v2/dept-purchasing" target="_blank">https://api.franklintn-gov.com/api/v2/dept-purchasing</a></td>
  </tr>
  <tr>
    <td>Engineering API <em>Proxy</em></td>
    <td><a href="https://dev.franklintn.gov/api/v1/eng" target="_blank">https://dev.franklintn.gov/api/v1/eng</a></td>
    <td>Proxy for <a href="https://api.franklintn-gov.com/api/v1/eng" target="_blank">https://api.franklintn-gov.com/api/v1/eng</a></td>
  </tr>
</table>

<h2 id="COFASV03">COFASV03</h2>
<p>DMZ Linux web server hosts publicly available frontend applications.</p>

<h3>Apps</h3>
<table>
  <tr>
    <th>Name</th>
    <th>URL</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Parking Availability</td>
    <td><a href="https://apps.franklintn.gov/parking-counter" target="_blank">https://apps.franklintn.gov/parking-counter</a></td>
    <td>Displays parking availability for 2nd Ave and 4th Ave parking garages.</td>
  </tr>
  <tr>
    <td>Active Construction Sites</td>
    <td><a href="https://apps.franklintn.gov/active-sites" target="_blank">https://apps.franklintn.gov/active-sites</a></td>
    <td>Mapping application displays active construction sites throughout the city.  Active sites are determined by Engineering and are maintained via the Stormwater site inspection application.</td>
  </tr>
  <tr>
    <td>Active CIP Projects</td>
    <td><a href="https://apps.franklintn.gov/active-projects" target="_blank">https://apps.franklintn.gov/active-projects</a></td>
    <td>Mapping application displays capital investment projects.  Active projects are determined by Engineering and are maintained via the internal CIP Tracker application.</td>
  </tr>
  <tr>
    <td>Indect Parking API <em>Proxy</em></td>
    <td><a href="https://apps.franklintn.gov/indect/structure" target="_blank">https://apps.franklintn.gov/indect/structure</a></td>
    <td>Proxy for <a href="https://api.franklintn-gov.com/indect/structure" target="_blank">https://api.franklintn-gov.com/indect/structure</a>.</td>
  </tr>
  <tr>
    <td>Engineering API <em>Proxy</em></td>
    <td><a href="https://apps.franklintn.gov/api/v1/eng" target="_blank">https://apps.franklintn.gov/api/v1/eng</a></td>
    <td>Proxy for <a href="https://api.franklintn-gov.com/api/v1/eng" target="_blank">https://api.franklintn-gov.com/api/v1/eng</a></td>
  </tr>  
</table>