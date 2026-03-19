Görev 2 — FriendList Task List
PHASE 1: JSON Dosyasını Oluştur
Task 1.1 — src/friends.json dosyasını oluştur:
json[
  {
    "avatar": "https://cdn-icons-png.flaticon.com/512/1998/1998592.png",
    "name": "Mango",
    "isOnline": true,
    "id": 1812
  },
  {
    "avatar": "https://cdn-icons-png.flaticon.com/512/616/616438.png",
    "name": "Kiwi",
    "isOnline": false,
    "id": 1137
  },
  {
    "avatar": "https://cdn-icons-png.flaticon.com/512/1623/1623681.png",
    "name": "Ajax",
    "isOnline": true,
    "id": 1213
  },
  {
    "avatar": "https://cdn-icons-png.flaticon.com/512/2977/2977285.png",
    "name": "Jay",
    "isOnline": true,
    "id": 1714
  },
  {
    "avatar": "https://cdn-icons-png.flaticon.com/512/1998/1998749.png",
    "name": "Poly",
    "isOnline": false,
    "id": 1284
  }
]

PHASE 2: FriendListItem Bileşenini Oluştur
Task 2.1 — src/components/FriendListItem/FriendListItem.jsx dosyasını oluştur:
jsximport styles from './FriendListItem.module.css';

const FriendListItem = ({ avatar, name, isOnline }) => {
  return (
    <div className={styles.item}>
      <img src={avatar} alt="Avatar" width="48" />
      <p className={styles.name}>{name}</p>
      <p className={isOnline ? styles.online : styles.offline}>
        {isOnline ? 'Online' : 'Offline'}
      </p>
    </div>
  );
};

export default FriendListItem;
Task 2.2 — src/components/FriendListItem/FriendListItem.module.css dosyasını oluştur:
css.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 16px;
  border: 1px solid #cccccc;
  border-radius: 8px;
  width: 120px;
}

.name {
  margin: 8px 0 4px;
  font-size: 18px;
  color: #111111;
}

.online {
  margin: 0;
  font-size: 14px;
  color: green;
}

.offline {
  margin: 0;
  font-size: 14px;
  color: red;
}

PHASE 3: FriendList Bileşenini Oluştur
Task 3.1 — src/components/FriendList/FriendList.jsx dosyasını oluştur:
jsximport FriendListItem from '../FriendListItem/FriendListItem';
import styles from './FriendList.module.css';

const FriendList = ({ friends }) => {
  return (
    <ul className={styles.list}>
      {friends.map(friend => (
        <li key={friend.id}>
          <FriendListItem
            avatar={friend.avatar}
            name={friend.name}
            isOnline={friend.isOnline}
          />
        </li>
      ))}
    </ul>
  );
};

export default FriendList;
Task 3.2 — src/components/FriendList/FriendList.module.css dosyasını oluştur:
css.list {
  display: flex;
  flex-direction: row;
  gap: 16px;
  list-style: none;
  margin: 24px 0;
  padding: 0;
}

PHASE 4: App Bileşenini Güncelle
Task 4.1 — src/App.jsx dosyasını tamamen şununla değiştir:
jsximport userData from './userData.json';
import friends from './friends.json';
import Profile from './components/Profile/Profile';
import FriendList from './components/FriendList/FriendList';

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
      <FriendList friends={friends} />
    </>
  );
};

export default App;

PHASE 5: Test ve Deploy
Task 5.1 — Çalıştır ve kontrol et:
bashnpm run dev
Tarayıcıda kontrol et:

Profile kartı hâlâ görünüyor mu? ✅
FriendList 5 kart yan yana görünüyor mu? ✅
Mango, Ajax, Jay → yeşil "Online" ✅
Kiwi, Poly → kırmızı "Offline" ✅
F12 Console → sıfır hata/uyarı ✅

Task 5.2 — Build al ve push et:
bashnpm run build
git add .
git commit -m "feat: add FriendList and FriendListItem components"
git push origin main