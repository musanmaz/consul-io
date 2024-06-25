# Consul Uploader CLI

Consul Uploader, belirli bir dizindeki konfigürasyon dosyalarını Consul KV store'a yüklemek için kullanılan bir CLI aracıdır.

## Kurulum

Bu projeyi çalıştırmak için Go'nun kurulu olması gerekmektedir. Go'yu [buradan](https://golang.org/dl/) indirebilirsiniz.

### Bağımlılıkların Yüklenmesi

Projenin bağımlılıklarını yüklemek için aşağıdaki komutları çalıştırın:

```sh
go get github.com/hashicorp/consul/api
go get github.com/spf13/cobra
go mod tidy
```

## Kullanım

CLI aracını çalıştırmak için aşağıdaki komutu kullanabilirsiniz:

```sh
go run main.go --consul-addr=http://localhost:8500 /path/to/config/directory
```

### Komut Satırı Argümanları

* `--consul-addr` : Consul sunucusunun adresini belirtir. Varsayılan değer `http://localhost:8500`'dir.

* `/path/to/config/directory` : Yüklemek istediğiniz konfigürasyon dosyalarının bulunduğu dizin.

## Örnek Kullanım

```sh
go run main.go --consul-addr=http://localhost:8500 test
```

Bu komut, `test` dizinindeki `.production` uzantılı dosyaları bulur ve Consul KV store'a yükler.


## Örnek Klasör Yapısı

```go
consul-uploader/
├── cmd/
│   └── root.go
├── test/
│   ├── team1/apps/
│   │   ├── project1/
│   │   │   └── .env.production
│   │   ├── project2/
│   │   │   └── appsettings.json.production
│   ├── team2/apps/
│   │   ├── project1/
│   │   │   └── .env.production
│   │   │   └── appsettings.json.production
├── go.mod
├── go.sum
└── main.go
```

* `cmd/:` CLI komutlarını içeren dosya.

* `test/:` Yüklemek istediğiniz konfigürasyon dosyalarının bulunduğu örnek dizin.

* `go.mod:` Go modül bilgilerini içeren dosya.

* `go.sum:` Go modüllerinin doğrulama bilgilerini içeren dosya.

* `main.go:` Programın giriş noktası.

## Bağımlılıklar

* [github.com/hashicorp/consul/api](https://github.com/hashicorp/consul/api) : Consul API ile iletişim kurmak için kullanılan kütüphane.

* [github.com/spf13/cobra](https://github.com/spf13/cobra) : Komut satırı arayüzü oluşturmak için kullanılan kütüphane.
