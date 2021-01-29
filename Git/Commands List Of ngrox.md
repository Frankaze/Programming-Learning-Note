# Commands List Of ngrox

## Avoid Bad Request 

When you browse website and it displays **Bad Request - Invalid Hostname**, please try to use below command: 

```bash
ngrok http -host-header=localhost 8080
```