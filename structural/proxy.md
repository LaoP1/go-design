# Proxy Pattern

The proxy pattern provides an object that controls access to another object, intercepting all calls.

## Implementation

```Golang
    package proxy

    // To use proxy and to object they must implement same methods
    type Subject interface {
        Request()
    }

    // Real objects what proxy will delegate
    type RealSubject struct {}

    // Request implements Subject interface and handle the real logic
    func (rs *RealSubject) Request() {
        fmt.Println("Get Request.")
    }

    // Proxy represents proxy object with intercepts actions
    type Proxy struct {
        subject *RealSubject
    }

    // Request are implemented Subject and intercepts action before send in real object
    func (p *Proxy) Request() {
        if p.subject == nil {
            p.subject = new(RealSubject)
        }
        p.subject.Request()
    }
```


## Usage
* Remote Proxy
* Virtual Proxy
* Protection Proxy
* Smart Reference