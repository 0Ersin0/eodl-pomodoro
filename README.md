# pomodorƎ (v2.6.0)

[![License](https://img.shields.io/badge/License-Apache_2.0-red.svg)](https://opensource.org/licenses/Apache-2.0)
[![Security-First](https://img.shields.io/badge/Security-Air--Gapped_Design-00f2fe.svg)](#-siber-güvenlik-ve-gizlilik-mimarisi-zero-trust--hardening)
[![Architecture](https://img.shields.io/badge/Architecture-Single--File_Vanilla-ff3131.svg)](#-teknik-yığın-ve-mimari)

**pomodorƎ**, siber güvenlik laboratuvarı estetiğiyle tasarlanmış, tam veri gizliliği ve Zero-Trust (Sıfır Güven) felsefesini benimseyen, süreleri tamamen özelleştirilebilir web tabanlı bir Pomodoro zamanlayıcıdır. **EO Digital Lab** çatısı altında, dış dünya ile bağı tamamen kesilmiş (Air-Gapped) çalışma prensiplerine uygun olarak ve üst düzey siber güvenlik sıkılaştırmalarıyla (Hardening) geliştirilmiştir.

---

## 🔒 Siber Güvenlik ve Gizlilik Mimarisi (Zero-Trust & Hardening)

Geleneksel web uygulamalarının aksine, `pomodorƎ` kullanıcı güvenliğini en üst düzeyde tutmak amacıyla her türlü dış veri sızıntısı ve siber saldırı vektörünü en baştan bloke eder:

* **Sıfır Dış İstek (Air-Gapped Operation):** Uygulama ilk yüklemeden sonra tamamen çevrimdışı (offline) çalışabilir. Tarayıcının `Network` sekmesinde dışarıya giden (CDNs, Google Fonts, harici API'ler vb.) tek bir HTTP/S isteği dahi tetiklenmez. IP sızıntısı ve DNS takibi riskini tamamen ortadan kaldırır.
* **CSP (Content Security Policy) Entegrasyonu:** HTML meta verisinde sıkılaştırılmış içerik güvenlik politikası (`default-src 'self'`) tanımlanmıştır. Bu sayede dış kaynaklı betiklerin enjekte edilmesi (XSS) donanımsal düzeyde engellenir.
* **Dinamik XSS Koruması:** Kullanıcı arayüzünde dinamik veri basılan tüm noktalarda strictly **`textContent`** kullanılmıştır. `innerHTML` kullanımı tamamen devre dışı bırakılarak tarayıcı tarafında zararlı script yürütme açıkları kapatılmıştır.
* **Prototype Pollution (Prototip Kirletmesi) Engeli:** Sistem yerel log nesnelerini (`dailyLogs`) işlerken ve oluştururken **`Object.create(null)`** yapısını kullanır. Bu sayede yerleşik nesne prototiplerinin sabote edilmesi engellenir.
* **Çerezsiz ve İzleyicisiz Yapı (No-Tracking):** Uygulama bünyesinde hiçbir çerez (cookie), takip pikseli veya analitik araç (Google Analytics vb.) barındırmaz. Kullanıcı profillemesi kesinlikle yapılmaz.
* **Kodla Sentezlenmiş Yerel Dijital Alarm:** Süre dolduğunda tetiklenen alarm sesi için dışarıdan bir `.mp3` veya `.wav` dosyası çağrılmaz. Ses, tarayıcının yerleşik **Web Audio API (`AudioContext`)** katmanı kullanılarak saf JavaScript kodlarıyla sıfırdan dijital olarak sentezlenir.

---

## 🎨 Yeni Profesyonel Modlar (Deployment Themes)

Arayüz, farklı odaklanma disiplinlerine ve estetik tercihlere göre optimize edilmiş 3 adet profesyonel mod sunar:

* **🔴 Admin Modu (Root) [Default]:** Koyu lacivert ve siber kırmızı (`#ff3131`) hatlarla tasarlanmış, sistem kontrolünün tamamen sizde olduğunu hissettiren siber güvenlik laboratuvarı teması.
* **🟢 Ares Modu (Tactical):** Karbon siyahı arka plan ve neon yeşil (`#00e676`) detaylarla donatılmış; dikkati dağıtacak her türlü unsuru bertaraf eden, taktiksel disiplin ve askeri odaklanma teması.
* **🟣 Orchid Modu (Aesthetic):** Koyu mor, pastel ametist (`#c084fc`) ve yumuşak lila tonlarında tasarlanmış; gözü yormayan, son derece modern, şık ve estetik çalışma alanı.

---

## 📊 İlerleme, Karar Yapıları ve Yerel Analitik (Local Gamification)

* **7 Günlük Yerel Loglama:** Tamamladığınız seanslar ve toplam çalışma süreleriniz, dış sunucular yerine tarayıcınızın izole güvenli belleğinde (`localStorage`) 7 günlük bir geçmiş analizi olarak tutulur.
* **Dinamik Başarı Rozetleri:** Seans sayılarınıza bağlı olarak aktif temaya uygun dinamik rozetler ve ilerleme durumları (Gamification) tetiklenir:
  * *Admin:* **Derin Odaklanma Ustası** (Simge: 🌱 / 🔥)
  * *Ares:* **Taktiksel Operasyon Lideri** (Simge: 🧭 / ⚡)
  * *Orchid:* **Zarafet ve Odak Elçisi** (Simge: 🌸 / 💜)
* **Mini Karar Protokolü (Decision Dialog):** Seans sonlarında karşınıza çıkan akıllı karar mekanizması, sonraki adıma (mola protokolü veya kesintisiz odaklanma) geçiş yapmanızı doğrudan klavye veya butonlar üzerinden yönetmenizi sağlar.

---

## 🎮 Klavye Kısayolları (Hotkeys)

Süreci klavyeden kesintisiz yönetebilmeniz için entegre kısayol haritası:
* **`Space` (Boşluk Tuşu):** Zamanlayıcıyı Başlat / Durdur
* **`R`:** Zamanlayıcıyı Sıfırla (Reset)
* **`1`:** Pomodoro Moduna Geç
* **`2`:** Kısa Mola Moduna Geç
* **`3`:** Uzun Mola Moduna Geç
* **`Escape`:** Aktif Modalları ve Dialog Pencerelerini Kapat

---

## 🛠️ Teknik Yığın ve Mimari

Uygulamanın hafifliği, yüksek performansı ve taşınabilirliği tamamen bağımlılıksız saf (Vanilla) teknolojilere dayanmasından gelir:

* **Frontend:** HTML5 (Semantik etiket yapısı)
* **Styling:** Modern CSS3, CSS Variables, Flexbox & Grid sistemleri
* **Core Engine:** Modern Vanilla JavaScript (ES6+), Web Audio API (`AudioContext`), `localStorage` API
* **Deployment:** GitHub Pages ve Jekyll motorunu devre dışı bırakan `.nojekyll` yapılandırması.

---

## 🚀 Kurulum ve Yerel Çalıştırma

Uygulama bağımsız ve tek bir `index.html` dosyasından oluştuğu için herhangi bir derleme (build) işlemine veya yerel sunucu kurulumuna gerek duymaz.

1. Projeyi klonlayın:
   ```bash
   git clone [https://github.com/0Ersin0/eodl-pomodoro.git](https://github.com/0Ersin0/eodl-pomodoro.git)
   ```
2. Proje dizinine gidin:
   ```bash
   cd eodl-pomodoro
   ```
3. `index.html` dosyasına çift tıklayarak, tamamen internet bağlantınız olmasa dahi tarayıcınız üzerinden güvenle kullanmaya başlayın.

---

## 📄 Lisans ve Telif Hakkı

Bu proje **Apache License 2.0** kapsamında lisanslanmıştır.

```text
Copyright 2026 EO Digital Lab

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
