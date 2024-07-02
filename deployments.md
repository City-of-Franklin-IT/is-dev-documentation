<h1>Deployments</h1>
<p>The following are application deployments from the IS Development team.  This list is maintained and should be considered the authoritative documentation for all IS Development related applications.</p>

<h2>COFASV30</h2>
<p>The primary duty of this host is to server Express applications used as the backend for most custom applications built by the IS team.  This server is behind the firewall and is reached by the public internet via proxy from COFASV32.  All Express applications are managed using PM2 daemon process manager that are accessed by dedicated port via Nginx reverse proxy.</p>

<h3>Apps</h3>
  <table>
    <tr>
      <th>Application Name</th>
      <th>URL</th>
      <th>PORT</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>dept-purchasing</td>
      <td><a href="https://api.franklin-gov.com/api/v2/dept-purchasing" target="_blank">https://api.franklin-gov.com/api/v2/dept-purchasing</a></td>
      <td>5000</td>
      <td>Handles database functionality for department purchasing application.</td>
    </tr>
    <tr>
      <td>rev-mgmt-tools</td>
      <td><a href="https://api.franklin-gov.com/rev-mgmt-tools" target="_blank">https://api.franklin-gov.com/rev-mgmt-tools</a></td>
      <td>5001</td>
      <td>Revenue Management Tools backend.</td>
    </tr>
    <tr>
      <td>indect</td>
      <td><a href="https://api.franklin-gov.com/indect/structure" target="_blank">https://api.franklin-gov.com/indect/structure</a></td>
      <td>5002</td>
      <td>Proxies requests to the Indect API for the parking garage availability application.</td>
    </tr>
    <tr>
      <td>eng-api</td>
      <td><a href="https://api.franklin-gov.com/api/v1/eng" target="_blank">https://api.franklin-gov.com/api/v1/eng</a></td>
      <td>5004</td>
      <td>Backend for multiple Engineering and Planning related applications.</td>
    </tr>
  </table>