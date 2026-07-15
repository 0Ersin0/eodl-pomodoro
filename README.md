# pomodorƎ (v2.6.0)

[![License](https://img.shields.io/badge/License-Apache_2.0-red.svg)](https://opensource.org/licenses/Apache-2.0)
[![Security-First](https://img.shields.io/badge/Security-Air--Gapped_Design-00f2fe.svg)](#-siber-güvenlik-ve-gizlilik-mimarisi-zero-trust--hardening)
[![Architecture](https://img.shields.io/badge/Architecture-Single--File_Vanilla-ff3131.svg)](#-teknik-yığın-ve-mimari)

**pomodorƎ**, siber güvenlik laboratuvarı estetiğiyle tasarlanmış, tam veri gizliliği ve Zero-Trust (Sıfır Güven) felsefesini benimseyen, süreleri tamamen özelleştirilebilir web tabanlı bir Pomodoro zamanlayıcıdır[cite: 2]. **EO Digital Lab** çatısı altında, dış dünya ile bağı tamamen kesilmiş (Air-Gapped) çalışma prensiplerine uygun olarak ve üst düzey siber güvenlik sıkılaştırmalarıyla (Hardening) geliştirilmiştir[cite: 2].

---

## 🔒 Siber Güvenlik ve Gizlilik Mimarisi (Zero-Trust & Hardening)

Geleneksel web uygulamalarının aksine, `pomodorƎ` kullanıcı güvenliğini en üst düzeyde tutmak amacıyla her türlü dış veri sızıntısı ve siber saldırı vektörünü en baştan bloke eder[cite: 2]:

* **Sıfır Dış İstek (Air-Gapped Operation):** Uygulama ilk yüklemeden sonra tamamen çevrimdışı (offline) çalışabilir[cite: 2]. Tarayıcının `Network` sekmesinde dışarıya giden (CDNs, Google Fonts, harici API'ler vb.) tek bir HTTP/S isteği dahi tetiklenmez[cite: 2]. IP sızıntısı ve DNS takibi riskini tamamen ortadan kaldırır[cite: 2].
* **CSP (Content Security Policy) Entegrasyonu:** HTML meta verisinde sıkılaştırılmış içerik güvenlik politikası (`default-src 'self'`) tanımlanmıştır[cite: 2]. Bu sayede dış kaynaklı betiklerin enjekte edilmesi (XSS) donanımsal düzeyde engellenir[cite: 2].
* **Dinamik XSS Koruması:** Kullanıcı arayüzünde dinamik veri basılan tüm noktalarda strictly **`textContent`** kullanılmıştır[cite: 2]. `innerHTML` kullanımı tamamen devre dışı bırakılarak tarayıcı tarafında zararlı script yürütme açıkları kapatılmıştır[cite: 2].
* **Prototype Pollution (Prototip Kirletmesi) Engeli:** Sistem yerel log nesnelerini (`dailyLogs`) işlerken ve oluştururken **`Object.create(null)`** yapısını kullanır[cite: 2]. Bu sayede yerleşik nesne prototiplerinin sabote edilmesi engellenir[cite: 2].
* **Çerezsiz ve İzleyicisiz Yapı (No-Tracking):** Uygulama bünyesinde hiçbir çerez (cookie), takip pikseli veya analitik araç (Google Analytics vb.) barındırmaz[cite: 2]. Kullanıcı profillemesi kesinlikle yapılmaz[cite: 2].
* **Kodla Sentezlenmiş Yerel Dijital Alarm:** Süre dolduğunda tetiklenen alarm sesi için dışarıdan bir `.mp3` veya `.wav` dosyası çağrılmaz[cite: 2]. Ses, tarayıcının yerleşik **Web Audio API (`AudioContext`)** katmanı kullanılarak saf JavaScript kodlarıyla sıfırdan dijital olarak sentezlenir[cite: 2].

---

## 🎨 Yeni Profesyonel Modlar (Deployment Themes)

Arayüz, farklı odaklanma disiplinlerine ve estetik tercihlere göre optimize edilmiş 3 adet profesyonel mod sunar[cite: 2]:

* **🔴 Admin Modu (Root) [Default]:** Koyu lacivert ve siber kırmızı (`#ff3131`) hatlarla tasarlanmış, sistem kontrolünün tamamen sizde olduğunu hissettiren siber güvenlik laboratuvarı teması[cite: 2].
* **🟢 Ares Modu (Tactical):** Karbon siyahı arka plan ve neon yeşil (`#00e676`) detaylarla donatılmış; dikkati dağıtacak her türlü unsuru bertaraf eden, taktiksel disiplin ve askeri odaklanma teması[cite: 2].
* **🟣 Orchid Modu (Aesthetic):** Koyu mor, pastel ametist (`#c084fc`) ve yumuşak lila tonlarında tasarlanmış; gözü yormayan, son derece modern, şık ve estetik çalışma alanı[cite: 2].

---

## 📊 İlerleme, Karar Yapıları ve Yerel Analitik (Local Gamification)

* **7 Günlük Yerel Loglama:** Tamamladığınız seanslar ve toplam çalışma süreleriniz, dış sunucular yerine tarayıcınızın izole güvenli belleğinde (`localStorage`) 7 günlük bir geçmiş analizi olarak tutulur[cite: 2].
* **Dinamik Başarı Rozetleri:** Seans sayılarınıza bağlı olarak aktif temaya uygun dinamik rozetler ve ilerleme durumları (Gamification) tetiklenir[cite: 2]:
  * *Admin:* **Derin Odaklanma Ustası** (Simge: 🌱 / 🔥)[cite: 2]
  * *Ares:* **Taktiksel Operasyon Lideri** (Simge: 🧭 / ⚡)[cite: 2]
  * *Orchid:* **Zarafet ve Odak Elçisi** (Simge: 🌸 / 💜)[cite: 2]
* **Mini Karar Protokolü (Decision Dialog):** Seans sonlarında karşınıza çıkan akıllı karar mekanizması, sonraki adıma (mola protokolü veya kesintisiz odaklanma) geçiş yapmanızı doğrudan klavye veya butonlar üzerinden yönetmenizi sağlar[cite: 2].

---

## 🎮 Klavye Kısayolları (Hotkeys)

Süreci klavyeden kesintisiz yönetebilmeniz için entegre kısayol haritası[cite: 2]:
* **`Space` (Boşluk Tuşu):** Zamanlayıcıyı Başlat / Durdur[cite: 2]
* **`R`:** Zamanlayıcıyı Sıfırla (Reset)[cite: 2]
* **`1`:** Pomodoro Moduna Geç[cite: 2]
* **`2`:** Kısa Mola Moduna Geç[cite: 2]
* **`3`:** Uzun Mola Moduna Geç[cite: 2]
* **`Escape`:** Aktif Modalları ve Dialog Pencerelerini Kapat[cite: 2]

---

## 🛠️ Teknik Yığın ve Mimari

Uygulamanın hafifliği, yüksek performansı ve taşınabilirliği tamamen bağımlılıksız saf (Vanilla) teknolojilere dayanmasından gelir[cite: 2]:

* **Frontend:** HTML5 (Semantik etiket yapısı)[cite: 2]
* **Styling:** Modern CSS3, CSS Variables, Flexbox & Grid sistemleri[cite: 2]
* **Core Engine:** Modern Vanilla JavaScript (ES6+), Web Audio API (`AudioContext`), `localStorage` API[cite: 2]
* **Deployment:** GitHub Pages ve Jekyll motorunu devre dışı bırakan `.nojekyll` yapılandırması[cite: 2].

---

## 🚀 Kurulum ve Yerel Çalıştırma

Uygulama bağımsız ve tek bir `index.html` dosyasından oluştuğu için herhangi bir derleme (build) işlemine veya yerel sunucu kurulumuna gerek duymaz[cite: 2].

1. Projeyi klonlayın:
   ```bash
   git clone [https://github.com/0Ersin0/eodl-pomodoro.git](https://github.com/0Ersin0/eodl-pomodoro.git)
   ```
2. Proje dizinine gidin:
   ```bash
   cd eodl-pomodoro
   ```
3. `index.html` dosyasına çift tıklayarak, tamamen internet bağlantınız olmasa dahi tarayıcınız üzerinden güvenle kullanmaya başlayın[cite: 2].

---

## 📄 Lisans ve Telif Hakkı

Bu proje **Apache License 2.0** kapsamında lisanslanmıştır[cite: 2].

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
