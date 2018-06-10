
# Debug
A tiny golang debugging utility modelled after go core's debugging technique.
Works in go with any things that implement io.Writer.

## Installation

`go get github.com/alexisvisco/Debug`

## Documentation

Functions:
* [`NewDebug(name string) *Debug`](#NewDebug(name string) *Debug)
* [`Register(name string) (*Debug, Err)`](#Register(name string) (*Debug, Err))
* [`Get(name string) (*Debug, Err)`](#Get(name string) (*Debug, Err))
* [`Delete(name string) Err`](#Delete(name string) Err)
* [`Enable()`](#Enable())
* [`Disable()`](#Disable())

Methods:
* [`(d *Debug) Print(message string)`](#Print)
* [`(d *Debug) Sprint(message string)`](#Print)


### NewDebug(name string) *Debug

__Description__:
Create a debug structure without registering it. Cannot be accessible with [`Get`](#Get).
Generate a random color from 31 to 37 and 91 to 97 as ainsi code.

```go
debug := debug.NewDebug("woaw") 
```

### Register(name string) (*Debug, Err)

__Description__:
Create a debug and registering it. Can be accessible with [`Get`](#Get).
[`NewDebug`](#NewDebug) is used to create the structure.

__Error__:
Return an error if name is already in the registery.

```go
debug, err := debug.Create("woaw")
if err {
  fmt.Printf("name %s already used !", "woaw")
}
```

### Get(name string) (*Debug, Err)

__Description__:
Get a debug structure from it name.

__Error__:
Return an error if name is not in the registery.

```go
debug, err := debug.Get("woaw")
if err {
  fmt.Printf("name %s has not been created !", "woaw")
}
```

### Delete(name string) Err

__Description__:
Delete a debug structure from the registery.

__Error__:
Return an error if name is not in the registery.

```go
err := debug.Delete("woaw")
if err {
  fmt.Printf("name %s has not been created !", "woaw")
}
```

### Enable()

__Description__:
Enable printing with debug.

```go
debug.Enable()
```

### Disable()

__Description__:
Disable printing with debug.

```go
debug.Disable()
```
