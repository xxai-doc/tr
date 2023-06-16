<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Dizine girdikten sonra önce nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ve ardından `direnv allow` kurulması önerilir (dizine girdikten sonra [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) otomatik olarak yürütülür).

Anlamı: Japonca'ya Çince çeviri, Korece, İngilizce, diğer tüm dillere İngilizce çeviri. Yalnızca Çince ve İngilizce'yi desteklemek istiyorsanız, `zh: en` yazmanız yeterlidir.

## ön uç kodu

* [ön uç kodu](https://github.com/xxai-art/web)
* [Bir bütün olarak site için dil paketleri](https://github.com/xxai-art/web/tree/main/i18n)
* [Oturum açma modülleri için dil paketleri](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Web Sitesi Çok Dilli Belgeler](https://github.com/xxai-doc)

Ön uç programlama dili, coffeescript sözdizimine dayalı olarak bazı özellikler ekleyen [@w5/kahve_plus](http://npmjs.com/@w5/coffee_plus) şeklindedir, bkz [. ./kahve_plus.md](./coffee_plus.md) .

## Web sitelerinin ve belgelerin uluslararası hale getirilmesi

Aşağıdaki 3 proje üzerine inşa edin

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Son ek `.mdt` , harici dosyalara başvurmak için `<+ ./coffee_plus/import.js>` benzer bir sözdizimi kullanabilir ve `.md` sonekiyle işaretleme oluşturabilirsiniz.

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown çevirisi, kodları ve bağlantıları çevirmez ve çevrilmiş cümleleri önbelleğe alır. Çeviri değiştirilmiş ancak orijinal metin değiştirilmemişse, yeniden yürütmek çeviri değişikliğinin üzerine yazmayacaktır.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  `yaml` tarafından oluşturulan web sitelerini çevirmek için dil dosyaları.

### Belge Çeviri Otomasyon Talimatları

[xxai-art/doc](https://github.com/xxai-art/doc) kod deposuna bakın

Dizine girdikten sonra önce nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ve ardından `direnv allow` kurulması önerilir (dizine girdikten sonra [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) otomatik olarak yürütülür).

Yüzlerce dile çevrilen büyük kod tabanından kaçınmak için her dil için ayrı bir kod tabanı oluşturdum ve kod tabanını depolamak için bir organizasyon oluşturdum.

`GITHUB_ACCESS_TOKEN` ortam değişkenini ayarlamak ve ardından [create.github.coffee'yi](https://github.com/xxai-art/doc/blob/main/create.github.coffee) çalıştırmak otomatik olarak kod havuzunu oluşturacaktır.

Elbette bunu bir kod tabanına da koyabilirsiniz.

Çeviri komut dosyası başvurusu [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Komut dosyası kodu aşağıdaki gibi yorumlanır:

[bunx](https://bun.sh/docs/cli/bunx) , daha hızlı olan npx'in yerini almıştır. Elbette, bun kurulu değilse, bunun yerine `npx` kullanabilirsiniz.

`bunx mdt zh` `.mdt` zh dizininde `.md` olarak işler, aşağıdaki bağlantılı 2 dosyaya bakın

* [kahve_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [kahve_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` çeviri için temel koddur (yalnızca kurulu `nodejs` varsa, ancak `bun` ve `direnv` kurulu değilse, çevirmek için `npx i18n` de çalıştırabilirsiniz).

[i18n.yml öğesini](https://github.com/xxai-art/doc/blob/main/i18n.yml) ayrıştırır, bu belgedeki `i18n.yml` yapılandırması aşağıdaki gibidir:

```
en:
zh: ja ko en
```

Anlamı: Japonca'ya Çince çeviri, Korece, İngilizce, diğer tüm dillere İngilizce çeviri. Yalnızca Çince ve İngilizce'yi desteklemek istiyorsanız, `zh: en` yazmanız yeterlidir.

Sonuncusu, bir `README.md` girişi oluşturmak için her dilin `README.md` dosyasının ana başlığı ile ilk alt başlığı arasındaki içeriği çıkaran [gen.README.kahve'dir](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) . Kod çok basit, kendiniz bakabilirsiniz.

Ücretsiz çeviri için Google API kullanılmaktadır. Google'a erişemiyorsanız, lütfen aşağıdaki gibi bir proxy yapılandırın ve ayarlayın:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Çeviri komut dosyası, `.i18n` dizininde çevrilmiş bir önbellek oluşturacaktır, lütfen bunu `git status` kontrol edin ve tekrarlanan çevirilerden kaçınmak için kod deposuna ekleyin.

Önbelleği güncellemek için çeviriyi her değiştirdiğinizde lütfen `bunx i18n` çalıştırın.

Orijinal metin ve çeviri aynı anda değiştirilirse önbellek karışacaktır, bu nedenle değiştirmek isterseniz yalnızca birini değiştirebilir ve ardından önbelleği güncellemek için `bunx i18n` çalıştırabilirsiniz.
