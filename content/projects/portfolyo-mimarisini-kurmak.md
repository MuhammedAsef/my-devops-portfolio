---
title: "Project: Building a DevOps Portfolio"
date: 2023-11-25
draft: false
tags: ["DevOps", "Hugo", "AWS", "CI/CD", "Git"]
summary: "Bu portfolyo sitesinin sıfırdan inşası, otomasyon süreçleri ve bulut mimarisi üzerine teknik notlarım."
---

## 🎯 Projenin Amacı
Bu proje, DevOps yetkinliklerimi sergilemek, modern web teknolojilerini deneyimlemek ve CI/CD süreçlerini uçtan uca (end-to-end) uygulamak amacıyla başlatıldı. Statik bir web sitesinin bulut tabanlı bir mimaride nasıl güvenli, hızlı ve otomatik bir şekilde sunulacağını göstermektedir.

## 🛠️ Teknoloji Yığını (Tech Stack)
Projede kullanılan araçlar ve seçim nedenlerim:

* **Hugo (Go tabanlı SSG):** HTML/CSS ile uğraşmak yerine içerik odaklı ve çok hızlı build süresi olduğu için seçtim.
* **Git & GitHub:** Versiyon kontrolü ve kaynak kod yönetimi için.
* **AWS S3 & CloudFront:** (Bunu yapınca dolduracağız) Serverless hosting ve CDN dağıtımı için.
* **GitHub Actions:** (Bunu yapınca dolduracağız) Deployment sürecini otomatize etmek için.

## Phase 1: Lokal Geliştirme Ortamı
İlk adımda yerel makinemde geliştirme ortamını kurdum.

1.  **Hugo Kurulumu:** Windows ortamına `Hugo Extended` sürümünü kurdum ve PATH ayarlarını yaptım.
2.  **Tema Seçimi:** Temiz kod yapısı ve hızı nedeniyle `PaperMod` temasını tercih ettim.
3.  **Git Init:** Projeyi versiyon kontrolüne aldım.

> **Karşılaşılan Sorun:** Hugo'nun standart sürümü PaperMod temasını derlerken hata verdi.
> **Çözüm:** `Hugo Extended` sürümüne geçiş yapılarak sorun çözüldü.

## Phase 2: Versiyon Kontrolü ve GitHub
Kodları GitHub'a taşırken `public` klasörünü `.gitignore` dosyasına ekledim. Bunun sebebi, derlenmiş dosyaları değil, sadece kaynak kodları (Source Code) saklamak istememdir. Derleme işlemini CI/CD pipeline'ı yapacak.

*(Buraya ileride GitHub repo linkini ve ekran görüntülerini ekleyebilirsin)*

## Phase 3: Cloud Mimarisi ve Deployment
*(Bunu AWS adımını yaparken dolduracağız)*

## 📈 Sonuç ve Kazanımlar
Bu proje sayesinde:
* Statik Site Üreteçlerinin (SSG) çalışma mantığını kavradım.
* Altyapı kurulumunu kodla yönetmeyi deneyimledim.
* Canlıya çıkış (Deployment) süreçlerini otomatize ettim.