### Proxy
```Golang
package proxy

type Subject interface {
	Request(action string)
}

type RealSubject struct {}

func (*RealSubject) Request(action string) {
	fmt.Printf("I can, %s", action)
}

type Proxy struct {
	subject *RealSubject
}

func (p *Proxy) Request(action string) {
	if p.subject == nil {
		p.subject = new(RealSubject)
	}
	if action == "Run" {
		p.subject.Request(action)
	}
}
```
