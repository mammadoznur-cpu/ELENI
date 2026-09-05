# ELENİ — Gerçek Admin V1

## Kurulum
1. GitHub'a bu klasörü yükleyin.
2. Netlify'da repository'yi site olarak bağlayın.
3. Netlify > Site configuration > Environment variables bölümüne şunları ekleyin:
   - ADMIN_PASSWORD = güçlü bir yönetici şifresi
   - GITHUB_OWNER = GitHub kullanıcı/organizasyon adı
   - GITHUB_REPO = repository adı
   - GITHUB_BRANCH = main
   - GITHUB_TOKEN = yalnızca repo içeriğini okuyup/yazabilen uygun GitHub token
4. Deploy edin.
5. `/admin/` adresine girin.

## Çalışma mantığı
Admin görseli Netlify Function'a gönderir. Function GitHub API ile görseli `assets/images/gallery/` içine commit eder ve `data/gallery.json` dosyasını günceller. Galeri sayfası bu JSON'u okur. Netlify yeni commit'i algılayıp siteyi yayınlar.

## Güvenlik
Token tarayıcıya gönderilmez; yalnızca Netlify Function ortamında tutulur. ADMIN_PASSWORD de server-side kontrol edilir. Üretimde güçlü, benzersiz şifre ve minimum yetkili GitHub token kullanın.
