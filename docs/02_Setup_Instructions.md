## Function Usage Instructions

### VoidChain Communication Architecture

**Edge Trust Machine Download Path:**

Windows Version:
```
http://www.xxx.com/download/tmac_win.rar
```

Linux:
```
http://www.xxx.com/download/tmac_linux.tar
```

### Usage Instructions

First configure the connection parameters in `chain.conf`:

- **Data_dir**: Existing data directory, no space requirements, occupies almost no space
- **tmac_entry**: VoidChain network trust machine access information

### Windows Startup Method
```
Drive:/pathname/guard_tmac.exe
```

### Linux Startup Method
```bash
nohup /pathname/guard_tmac.exe &
```

### Postman Interface Operation Method

If using local machine, the interface address is:
```
http://127.0.0.1:8080
```
