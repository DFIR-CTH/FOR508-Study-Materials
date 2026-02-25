
## Practical Approach to tracking account usage :

**We get information of Account Usage from the given Event-Ids.**

**Event-IDs :**

(i) **4624** = Successful Logon

(ii) **4625** = Failed Logon

(iii) **4634** / **4647** = Successful Logoff

(iv) **4648** = Logon using explicit Credential ( RunAs )

(v) **4672** = Special privileges assigned to new logon



**Run Powershell as an Administrator** 

[.1.]

```bash

Get-WinEvent -LogName Security | Where-Object Id -eq <event-id> 

```

[.2.] 

--> Efficient , Fast and Reliable then 1 

```bash

Get-WinEvent  -FilterHashTable @{ LogName = 'security' ; Id = <event-id> }

```

[.3.]

--> Filtering command to get details of Logon sessions 

> !NOTE
> Most useful for interactive logons ( Logon Type = 2 )

```bash

 Get-WinEvent -LogName Security -MaxEvent 5000 | Where-Object { $_.Id -eq 4624 -or $_.Id -eq 4647 } | Select-Object TimeCreated , Id ,User

 ```

 or 

 **Advance Commands Which is efficient and reliable then normal command** 

 [.3.1.]

--> Commands to get information of User loggon on using ( Logon Type = 2 or 10 ; and Event ID = 4624 )

> !NOTE
> Logon Type : 2 =  Interactive logons and 10 = RDP logons

```bash

Get-WinEvent -LogName Security | Where-Object { $_.Id -eq 4624  -and $_.Properties[8].Value -eq 2  } | Select-Object TimeCreated , Id

 ```

> !NOTE
> Here , 
>
> $_Properties.Value means that, in the Details tab in Event Viewer, the EventData list starts from index ; the Logon Type property is at index , so we filter by the LogonType value.

 
or 

 ```bash

  Get-WinEvent -LogName Security -MaxEvent 500 | Where-Object { $_.Id -eq 4624  -and $_.Properties[8].Value -eq 2  } | Select-Object TimeCreated , Id 

  ```

  -MaxEvent 500 = Get info upto 500 events { you can change number as per your requirements }

  [.3.2.]

  --> The  given command gives similar output like [.3.1.] but `Faster` then [.3.1.] 

  ```bash

  Get-WinEvent -FilterHashTable @{ LogName = 'security' ; Id = 4624 } | Where-Object { $_.Properties[8].value -eq 2 } | Select-Object TimeCreated , Id

  ```
  

