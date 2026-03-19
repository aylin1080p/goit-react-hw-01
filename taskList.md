📋 goit-react-hw-01 — Task List
PHASE 1: Proje Yapısını Hazırla
Task 1.1 — Klasör yapısını oluştur
src/components/Profile/ klasörünü oluştur
Task 1.2 — userData.json dosyasını oluştur
src/userData.json dosyası oluştur, içeriği tam olarak şu olsun:
json{
  "username": "Jacques Gluke",
  "tag": "jgluke",
  "location": "Ocho Rios, Jamaica",
  "avatar": "https://cdn-icons-png.flaticon.com/512/2922/2922506.png",
  "stats": {
    "followers": 5603,
    "views": 4827,
    "likes": 1308
  }
}

PHASE 2: Profile Bileşenini Oluştur
Task 2.1 — src/components/Profile/Profile.jsx dosyasını oluştur
Tam içerik:
jsximport styles from './Profile.module.css';

const Profile = ({ name, tag, location, image, stats }) => {
  return (
    <div className={styles.card}>
      <div className={styles.info}>
        <img src={image} alt="User avatar" className={styles.avatar} />
        <p className={styles.name}>{name}</p>
        <p className={styles.tag}>@{tag}</p>
        <p className={styles.location}>{location}</p>
      </div>

      <ul className={styles.statsList}>
        <li className={styles.statsItem}>
          <span className={styles.label}>Followers</span>
          <span className={styles.value}>{stats.followers}</span>
        </li>
        <li className={styles.statsItem}>
          <span className={styles.label}>Views</span>
          <span className={styles.value}>{stats.views}</span>
        </li>
        <li className={styles.statsItem}>
          <span className={styles.label}>Likes</span>
          <span className={styles.value}>{stats.likes}</span>
        </li>
      </ul>
    </div>
  );
};

export default Profile;
Task 2.2 — src/components/Profile/Profile.module.css dosyasını oluştur
Tam içerik:
css.card {
  width: 380px;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  background-color: #ffffff;
}

.info {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 24px 16px;
  background-color: #f8f8f8;
}

.avatar {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  margin-bottom: 16px;
}

.name {
  margin: 0 0 4px;
  font-size: 20px;
  font-weight: 700;
  color: #111111;
}

.tag {
  margin: 0 0 4px;
  font-size: 16px;
  color: #888888;
}

.location {
  margin: 0;
  font-size: 16px;
  color: #888888;
}

.statsList {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  border-top: 1px solid #dddddd;
}

.statsItem {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 16px 8px;
  border-right: 1px solid #dddddd;
}

.statsItem:last-child {
  border-right: none;
}

.label {
  font-size: 14px;
  color: #555555;
  margin-bottom: 4px;
}

.value {
  font-size: 18px;
  font-weight: 700;
  color: #111111;
}

PHASE 3: App Bileşenini Güncelle
Task 3.1 — src/App.jsx dosyasını tamamen şununla değiştir:
jsximport userData from './userData.json';
import Profile from './components/Profile/Profile';

const App = () => {
  return (
    <>
      <Profile
        name={userData.username}
        tag={userData.tag}
        location={userData.location}
        image={userData.avatar}
        stats={userData.stats}
      />
    </>
  );
};

export default App;

PHASE 4: Prettier Kurulumu ve Formatlama
Task 4.1 — Prettier'ı yükle (zaten yoksa)
bashnpm install --save-dev prettier
Task 4.2 — .prettierrc dosyasını proje kök dizininde oluştur:
json{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
Task 4.3 — Tüm JS/JSX dosyalarını formatla:
bashnpx prettier --write "src/**/*.{js,jsx}"

PHASE 5: Kontrol ve Temizlik
Task 5.1 — src/App.css ve src/index.css içeriğini kontrol et
src/App.css varsa içini tamamen boşalt veya sil.
src/index.css varsa sadece temel reset bırak:
css*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: sans-serif;
}
Task 5.2 — src/main.jsx dosyasını kontrol et, şu şekilde olmalı:
jsximport { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import './index.css';
import App from './App.jsx';

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>
);

PHASE 6: Local Test
Task 6.1 — Projeyi çalıştır ve konsolu kontrol et:
bashnpm run dev
Tarayıcıda http://localhost:5173 aç → DevTools Console'da hata/uyarı sıfır olmalı.

PHASE 7: Build ve Deploy
Task 7.1 — Production build al:
bashnpm run build
Hata yoksa devam et.
Task 7.2 — Tüm değişiklikleri commit et ve push et:
bashgit add .
git commit -m "feat: add Profile component with CSS modules and userData.json"
git push origin main
Vercel otomatik deploy edecek. Deploy tamamlanınca Vercel URL'ini kontrol et — aynı şekilde konsol hatasız olmalı.