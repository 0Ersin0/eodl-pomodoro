# pomodorƎ (v1.0.0)

[![License](https://img.shields.io/badge/License-Apache_2.0-red.svg)](https://opensource.org/licenses/Apache-2.0)
[![Security-First](https://img.shields.io/badge/Security-Air--Gapped_Design-00f2fe.svg)](#-siber-güvenlik-ve-gizlilik-mimarisi-zero-trust)
[![Architecture](https://img.shields.io/badge/Architecture-Single--File_Vanilla-ff3131.svg)](#-teknik-yığın-ve-mimari)

**pomodorƎ**, siber güvenlik laboratuvarı estetiğiyle tasarlanmış, tam veri gizliliği ve Zero-Trust (Sıfır Güven) felsefesini benimseyen, süreleri tamamen özelleştirilebilir web tabanlı bir Pomodoro zamanlayıcıdır. **EO Digital Lab** çatısı altında, dış dünya ile bağı tamamen kesilmiş (Air-Gapped) çalışma prensiplerine uygun olarak geliştirilmiştir.

---

## 🔒 Siber Güvenlik ve Gizlilik Mimarisi (Zero-Trust)

Geleneksel web uygulamalarının aksine, `pomodorƎ` kullanıcı güvenliğini en üst düzeyde tutmak amacıyla her türlü dış veri sızıntısı vektörünü en baştan bloke eder:

* **Sıfır Dış İstek (Air-Gapped Operation):** Uygulama ilk yüklemeden sonra tamamen offline çalışabilir. Tarayıcının `Network` sekmesinde dışarıya giden (CDNs, Google Fonts, FontAwesome, harici API'ler) tek bir HTTP/S isteği dahi tetiklenmez. IP sızıntısı riskini tamamen ortadan kaldırır.
* **Çerezsiz ve İzleyicisiz Yapı (No-Tracking):** Uygulama bünyesinde hiçbir çerez (cookie), takip pikseli, oturum kaydedici veya analitik araç (Google Analytics, Hotjar vb.) barındırmaz. Kullanıcı profillemesi yapılmaz.
* **İzole Yerel Hafıza (Local-Only State):** Kullanıcının özelleştirdiği çalışma ve mola süreleri, herhangi bir bulut veritabanı yerine tarayıcının yerel ve izole güvenli hafızasında (`localStorage`) saklanır.
* **Kodla Sentezlenmiş Dijital Alarm:** Süre dolduğunda tetiklenen alarm sesi için dışarıdan bir `.mp3` veya `.wav` dosyası çağrılmadığından (bu işlem bir dış istek vektörüdür) ses, tarayıcının yerleşik **AudioContext API** katmanı kullanılarak saf JavaScript kodlarıyla sıfırdan sentezlenir. Yarım saniye arayla üç kez tekrarlayan ritmik bir dijital masa saati alarmı üretilir.

---

## 🎨 Tasarım ve Laboratuvar Estetiği

Arayüz, uzun çalışma seanslarında gözü yormayacak ve odaklanmayı artıracak siber güvenlik laboratuvarı (Digital Lab) temasına sadık kalınarak geliştirilmiştir:

* **Derin Uzay Siyahı (`#050816`)** ana arka planı ve **Slate Surface (`#0f172a`)** panelleriyle göz sağlığını korur.
* Zamanlayıcı moduna göre dinamik renk geçişleri sunar: Çalışma periyodunda **Neon Kırmızı (`#ff3131`)**, mola periyotlarında ise **Elektrik Siyan/Mavi (`#00f2fe`)** vurguları aktiftir.
* Görsel titremeleri ve UI kaymalarını önlemek adına, sayaç rakamlarında tamamen sabit genişlikli **Monospaced Font Stack** mimarisi kullanılmıştır.

---

## 🛠️ Teknik Yığın ve Mimari

Uygulamanın esnekliği, kararlılığı ve hafifliği tamamen saf (Vanilla) teknolojilere dayanmasından gelir:

* **Frontend:** HTML5, Semantik Etiket Yapısı
* **Styling:** Modern CSS3, CSS Variables (Custom Properties), Flexbox & Grid Layouts
* **Core Engine:** Modern Vanilla JavaScript (ES6+), Web Audio API (`AudioContext`), `localStorage` API
* **Deployment:** GitHub Pages & Devre Dışı Bırakılmış Jekyll Motoru (`.nojekyll`) ile sıfır derleme/build maliyeti.

---

## 🚀 Kurulum ve Yerel Çalıştırma

Uygulama bağımsız ve tek bir `index.html` dosyasından oluştuğu için herhangi bir paket yöneticisine (npm, yarn) veya yerel sunucuya ihtiyaç duymaz.

1.  Projeyi klonlayın:
    ```bash
    git clone [https://github.com/0Ersin0/eodl-pomodoro.git](https://github.com/0Ersin0/eodl-pomodoro.git)
    ```
2.  Proje dizinine gidin:
    ```bash
    cd eodl-pomodoro
    ```
3.  `index.html` dosyasına çift tıklayarak tamamen internet bağlantınız olmasa bile tarayıcınız üzerinden güvenle kullanmaya başlayın.

---

## 📄 Lisans ve Telif Hakkı

Bu proje **Apache License 2.0** kapsamında lisanslanmıştır. 

```text
Copyright 2026 Ersin Özüdoğru (EO Digital Lab)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.