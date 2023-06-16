<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.sanat

Web sitesi kodunun bir kısmı açık kaynak kodludur, çeviriyi optimize etmeye yardımcı olmaktan memnuniyet duyarız.

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
