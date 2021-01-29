This test represents a very simple scale out scenario.

I have simple XP1 installation and want to add extra CD instance. Request to xp1cd.localhost/ should be load balanced to one of the CD instances.



**Scale out instruction:**

```powershell
docker-compose up -d --scale cd=2
```



**Code for testing:**

```asp
<script runat="server">
    void Page_Load(object sender, System.EventArgs e) 
    {
        Response.Write(System.Environment.MachineName);
    }
</script>
```

The code should output MachineName (which will be container id) on each request. Test shows that instances are selected in round robin manner.