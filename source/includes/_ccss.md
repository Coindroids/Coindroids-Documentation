
# CCSS Compliance 

The [CCSS](https://cryptoconsortium.github.io/CCSS/) is an open security standard curated by [C4](https://cryptoconsortium.org). The original matrix can be found [here](https://cryptoconsortium.github.io/CCSS/Matrix/). 

The details below are the current results of our self-evaluation and in some cases reflect our intentions upon launch and not our currently implemented aspects. This document allows us to be open in our how we secure our platform, while also providing a case study for the CCSS.  


Our current security grade is *Uncertified*, our target is *Level I*. Our rebuttal of this marking is provided within related matrix sections. 

<table >
<thead>
  <tr>
    <th id='header_category'>Category</th>
    <th id='header_aspect'>Aspect</th>
    <th id='header_component'>Component</th>
    <th id='header_uncertifiable'>Uncertified</th>
    <th id='header_level_i'>Level</th>
    <th id='header_level_ii'>Level II</th>
    <th id='header_level_iii'>Level III</th>
  </tr>
</thead>
<tbody>
  
    
    <tr>
      

      
        
        

        <td rowspan=28>Cryptographic Asset Management</li>

      

      <td rowspan=3>Key / Seed Generation</td>

      
        
        <td>Operator-created Key / Seed</td>
        <td>Keys/seeds are issued to the keyholder by another actor</td>
        <td></td>
        <td></td>
        <td>Keys/seeds are created by the key/seed operator themselves</td>
        </tr>
        
      
        
          <tr>
        
        <td>Creation methodology is validated</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed creation methodology is validated prior to use</td>
        </tr>
        
      
        
          <tr>
        
        <td>DRBG Compliance</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed is created using a NIST SP 800-90A compliant DRBG that has been seeded with multiple cryptographically-secure sources of entropy</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=6>Wallet Creation</td>

      
        
        <td>Unique address per transaction</td>
        <td>Wallets/addresses are reused for system addresses, including Attack, Item Purchase, Change and Cold storage. Static addresses for Attack addresses, despite being against the CCSS guidelines, is needed for gameplay mechanics. Other addresses are static to provider a more efficient backend as every additional address monitored is can be a large tax on the system. <br> We are not convinced that address re-use is a security hazard as long as deterministic k values are used during signing.  </td>
        <td></td>
        <td></td>
        <td>Users can choose to use unique addresses for every transaction sent into the Coindroids system.</td>
        </tr>
        
      
        
          <tr>
        
        <td>Multiple keys for signing</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Transactions require signatures from 2 or more keys</td>
        </tr>
        
      
        
          <tr>
        
        <td>Redundant key for recovery</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Redundant keys are assigned for recovery purposes (i.e. 2of3, 3of5, etc.)</td>
        </tr>
        
      
        
          <tr>
        
        <td>Deterministic wallets</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Addresses are assigned deterministically</td>
        </tr>
        
      
        
          <tr>
        
        <td>Geographic distribution of keys</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Keys are distributed across multiple separate locations</td>
        </tr>
        
      
        
          <tr>
        
        <td>Organizational distribution of keys</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=7>Key Storage</td>

      
        
        <td>Primary keys are stored encrypted</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed is stored with strong encryption</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key exists</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed backup is stored in a separate location from primary key/seed</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key has environmental protection</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed backup is protected from environmental damage</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key is access-controlled</td>
        <td></td>
        <td></td>
        <td>Key/seed backup is protected by access controls to prevent unauthorized access (i.e. safe/safe deposit box)</td>
        <td>Key/seed backup is protected by access controls to prevent unauthorized access (i.e. safe/safe deposit box)</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key has tamper-evident seal</td>
        <td></td>
        <td></td>
        <td>Key/seed backup employs tamper-evident seal</td>
        <td>Key/seed backup employs tamper-evident seal</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key is encrypted</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed backup is stored with strong encryption equal/better than that used to protect primary key</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup key is protected from EMP</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed backup is resistant to ElectroMagnetic Pulses (EMPs)</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=8>Key Usage</td>

      
        
        <td>Key access requires user/pass/nth factor</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Access to key/seed requires an identifier and at least 3 other factors (password, MFA token, in-person verification by guard, IP address whitelist, physical key to gain access to secured storage, countersigning organization)</td>
        </tr>
        
      
        
          <tr>
        
        <td>Keys are only used in a trusted environment</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Keys/seeds are only used in trusted environments</td>
        </tr>
        
      
        
          <tr>
        
        <td>Operator reference checks</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed holders have references checked</td>
        </tr>
        
      
        
          <tr>
        
        <td>Operator ID checks</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Key/seed holders have identify verified</td>
        </tr>
        
      
        
          <tr>
        
        <td>Operator background checks</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        </tr>
        
      
        
          <tr>
        
        <td>Spends are verified before signing</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Verification of fund destinations and amounts are performed prior to key usage</td>
        </tr>
        
      
        
          <tr>
        
        <td>No two keys are used on one device</td>
        <td></td>
        <td></td>
        <td></td>
        <td>No two keys belonging to the same wallet are present on any one device</td>
        </tr>
        
      
        
          <tr>
        
        <td>DRBG Compliance</td>
        <td></td>
        <td></td>
        <td></td>
        <td>The 'k' values in digital signatures are created using a NIST SP 800-90A compliant DRBG OR The 'k' values are created deterministically according to RFC 6979</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=2>Key Compromise Protocol (KCP)</td>

      
        
        <td>KCP Exists</td>
        <td></td>
        <td></td>
        <td></td>
        <td>A written checklist/procedure document exists that outlines procedures for each actor to carry out in order to remove the risk of compromise. Document is maintained as warranted by changes to the system.</td>
        </tr>
        
      
        
          <tr>
        
        <td>KCP Training + Rehearsals</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Regular training is provided to keyholders to ensure they are prepared to invoke the protocol when required.</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=2>Keyholder Grant/Revoke Policies & Procedures</td>

      
        
        <td>Grant/Revoke Procedures/Checklist</td>
        <td></td>
        <td></td>
        <td></td>
        <td>A written checklist/procedure document exists that is followed for on/offboarding. The checklist outlines every permission to grant/revoke for every role in the information system</td>
        </tr>
        
      
        
          <tr>
        
        <td>Grant/Revoke Audit Trail</td>
        <td></td>
        <td></td>
        <td></td>
        <td>An audit trail records every change of access including who performed the change</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      
        
        

        <td rowspan=9>Operations</li>

      

      <td rowspan=1>Security Audits / Pentests</td>

      
        
        <td>Security Audit</td>
        <td></td>
        <td></td>
        <td>A security audit has been completed by another entity who did not assist in the development of the system</td>
        <td>External security audits are conducted regularly (at least 1/yr)</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=2>Data Sanitization Policy (DSP)</td>

      
        
        <td>DSP Exists</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Detailed policy covering sanitization requirements, procedures, and validation steps for every media type used by business</td>
        </tr>
        
      
        
          <tr>
        
        <td>Audit Trail of all media sanitization</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Audit trails are maintained for every piece of sanitized media</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=1>Proof of Reserve (PoR)</td>

      
        
        <td>Proof of Reserve Audits</td>
        <td></td>
        <td></td>
        <td></td>
        <td>The ledger is openly viewable by all, so no PoR audits are necessary</td>
        </tr>
        
      

    </tr>
  
    
    <tr>
      

      

      <td rowspan=2>Audit Logs</td>

      
        
        <td>Application Audit Logs</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Full audit trail exists of all user/admin actions</td>
        </tr>
        
      
        
          <tr>
        
        <td>Backup of Audit Logs</td>
        <td></td>
        <td></td>
        <td></td>
        <td>Backups of audit data are performed regularly</td>
        </tr>
        
      

    </tr>
  
</tbody>
</table>
