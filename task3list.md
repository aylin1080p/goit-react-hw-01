Görev 3 — TransactionHistory Task List
PHASE 1: JSON Dosyasını Oluştur
Task 1.1 — src/transactions.json dosyasını oluştur:
json[
  {
    "id": "1e0700a2-5183-4291-85cc-2065a036a683",
    "type": "invoice",
    "amount": "964.82",
    "currency": "LRD"
  },
  {
    "id": "a30f821b-4d25-4ff0-abdd-e340b3f0dd2b",
    "type": "payment",
    "amount": "686.50",
    "currency": "WST"
  },
  {
    "id": "44dca67a-8e5a-4798-bf8e-b15efd4e1abd",
    "type": "invoice",
    "amount": "828.62",
    "currency": "UGX"
  },
  {
    "id": "ea8ed3dc-2b68-4a53-905a-53ecb0adef33",
    "type": "withdrawal",
    "amount": "527.80",
    "currency": "ALL"
  },
  {
    "id": "63ca02f9-d637-46b5-9237-f3b24425e029",
    "type": "payment",
    "amount": "862.44",
    "currency": "AUD"
  },
  {
    "id": "ed0263e8-59a5-4bf1-87e0-2bb88e53dc34",
    "type": "withdrawal",
    "amount": "907.00",
    "currency": "GEL"
  },
  {
    "id": "4eaab41b-b967-40ac-82ed-85fc66f646f1",
    "type": "deposit",
    "amount": "103.10",
    "currency": "BWP"
  },
  {
    "id": "9648a350-8469-42d5-8bf3-18090de5fe67",
    "type": "withdrawal",
    "amount": "322.32",
    "currency": "MRO"
  },
  {
    "id": "9c5c25fb-1a95-4b2f-8d1f-4c4426d677cc",
    "type": "invoice",
    "amount": "14.79",
    "currency": "PYG"
  }
]

PHASE 2: TransactionHistory Bileşenini Oluştur
Task 2.1 — src/components/TransactionHistory/TransactionHistory.jsx dosyasını oluştur:
jsximport styles from './TransactionHistory.module.css';

const TransactionHistory = ({ items }) => {
  return (
    <table className={styles.table}>
      <thead className={styles.thead}>
        <tr>
          <th className={styles.th}>Type</th>
          <th className={styles.th}>Amount</th>
          <th className={styles.th}>Currency</th>
        </tr>
      </thead>
      <tbody>
        {items.map((item, index) => (
          <tr
            key={item.id}
            className={index % 2 === 0 ? styles.rowEven : styles.rowOdd}
          >
            <td className={styles.td}>
              {item.type.charAt(0).toUpperCase() + item.type.slice(1)}
            </td>
            <td className={styles.td}>{item.amount}</td>
            <td className={styles.td}>{item.currency}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
};

export default TransactionHistory;
Task 2.2 — src/components/TransactionHistory/TransactionHistory.module.css dosyasını oluştur:
css.table {
  width: 100%;
  border-collapse: collapse;
  margin: 24px 0;
}

.thead {
  background-color: #2e2e2e;
  color: #ffffff;
}

.th {
  padding: 12px 16px;
  text-align: center;
  font-weight: 700;
  font-size: 15px;
}

.td {
  padding: 12px 16px;
  text-align: center;
  font-size: 15px;
  color: #111111;
}

.rowEven {
  background-color: #ffffff;
}

.rowOdd {
  background-color: #e8e8e8;
}

PHASE 3: App Bileşenini Güncelle
Task 3.1 — src/App.jsx dosyasını tamamen şununla değiştir:
jsximport userData from './userData.json';
import friends from './friends.json';
import transactions from './transactions.json';
import Profile from './components/Profile/Profile';
import FriendList from './components/FriendList/FriendList';
import TransactionHistory from './components/TransactionHistory/TransactionHistory';

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
      <TransactionHistory items={transactions} />
    </>
  );
};

export default App;

PHASE 4: Test ve Deploy
Task 4.1 — Çalıştır ve kontrol et:
bashnpm run dev
Tarayıcıda kontrol et:

Profile kartı görünüyor mu? ✅
FriendList 5 kart görünüyor mu? ✅
TransactionHistory tablosu görünüyor mu? ✅
Tablo başlığı koyu/siyah arka plan: Type / Amount / Currency ✅
9 satır veri var mı? ✅
Çift/tek satırlar zebra rengi (beyaz/gri) ✅
type değerleri büyük harfle başlıyor mu? (invoice → Invoice) ✅
F12 Console → sıfır hata/uyarı ✅

Task 4.2 — Build al ve push et:
bashnpm run build
git add .
git commit -m "feat: add TransactionHistory component"
git push origin main