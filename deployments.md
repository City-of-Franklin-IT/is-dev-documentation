<h1>Deployments</h1>
<p>The following are application deployments from the IS Development team.  This list is maintained and should be considered the authoritative documentation for all IS Development related applications.</p>

<h2>COFASV30</h2>
<p>The primary duty of this host is to server Express applications used as the backend for most custom applications built by the IS team.  This server is behind the firewall and is reached by the public internet via proxy from COFASV32.  All Express applications are managed using PM2 daemon process manager that are accessed by dedicated port via Nginx reverse proxy.</p>

<h3>Apps</h3>
  <ul>
    <li>eng-api | <a href="https://api.franklin-gov.com/api/v1/eng" target="_blank">https://api.franklin-gov.com/api/v1/eng</a> | PORT = 5000</li>
  </ul>