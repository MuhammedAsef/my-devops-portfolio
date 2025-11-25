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

## Phase 3: Cloud Mimarisi (AWS)
Sitenin barındırılması (Hosting) için sunucu kiralama maliyetinden kaçınmak ve yüksek performans sağlamak amacıyla **Serverless** bir mimari kurdum.

* **Amazon S3:** Statik dosyaları (HTML/CSS/JS) depolamak için yapılandırıldı. "Static Website Hosting" özelliği aktif edildi.
* **Amazon CloudFront (CDN):** S3 bucket'ının önüne konumlandırıldı. Bu sayede:
    * Siteye **HTTPS (SSL)** sertifikası eklendi.
    * İçerikler dünya genelindeki Edge Location'lara dağıtıldı (Düşük gecikme süresi).
    * HTTP istekleri otomatik olarak HTTPS'e yönlendirildi.

## Phase 4: CI/CD Otomasyonu (GitHub Actions)
Manuel deployment hatalarını önlemek için **Continuous Deployment (CD)** süreci tasarlandı.

1.  **IAM & Security:** AWS üzerinde `github-actions-deployer` adında kısıtlı yetkilere sahip (Least Privilege) bir servis kullanıcısı oluşturuldu.
2.  **GitHub Secrets:** Hassas veriler (Access Key, Secret Key, Bucket ID) repoya düz metin olarak değil, şifreli Secret olarak eklendi.
3.  **Pipeline Workflow:** `.github/workflows/deploy.yml` dosyası ile şu adımlar otomatize edildi:
    * Checkout Code (Kodun çekilmesi)
    * Setup Hugo (Hugo ortamının kurulması)
    * Build & Minify (Sitenin derlenmesi)
    * Sync to S3 (Değişen dosyaların S3'e yüklenmesi)
    * Invalidate CloudFront Cache (CDN önbelleğinin temizlenmesi)

Artık her `git push` işleminde sitem 1 dakika içinde canlıya alınmaktadır. 🚀

## 📈 Sonuç ve Kazanımlar
Bu proje sayesinde:
* Statik Site Üreteçlerinin (SSG) çalışma mantığını kavradım.
* Altyapı kurulumunu kodla yönetmeyi deneyimledim.
* Canlıya çıkış (Deployment) süreçlerini otomatize ettim.