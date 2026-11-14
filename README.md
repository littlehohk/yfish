# yfish — CYD Aquarium / CYD 水族箱

**English · 繁體中文** — One browser game with an **instant language switch**. The single `index.html` provides both languages. You can change language at any time using the **繁體中文 / English** button at the top of the game, without restarting the fish or losing progress.

**Play / 開始遊玩:** https://littlehohk.github.io/yfish/

This mobile-friendly virtual aquarium is adapted from the ESP32 [CYD-Aquarium](https://github.com/littlehohk/CYD-Aquarium) project. It runs on iPhone browsers such as Brave and Safari, as well as desktop browsers, without any installation or build step.

---

## English

### How to play

- **Tap the water** to release one pellet for the golden minnow. After surviving seven days, it becomes a golden sea snake and eats small living fish instead.
- **Swipe inside the aquarium** to play or scare the animal.
- **AirCon** cools the tank; **Heater** warms it. Only one operates at a time. Tap an active control again to turn it off.
- **Light** toggles the aquarium lamp and counts as one play action. With the lamp off, the aquarium follows day/night brightness for the selected location.
- **Settings** allows you to search for a city, obtain live weather, set a manual outdoor-temperature fallback, and read the game rules.
- **After death**, hold the bottom NEW FISH area for two seconds to start a new life.

### Rules and survival

| Condition | Rule |
| --- | --- |
| Starting values | Hunger 2.5, boredom 2.5, age zero |
| Natural increase | Both indices rise by 0.1 every 20 minutes |
| Food eaten | Reduces hunger by 0.1 |
| Swipe or accepted light toggle | Reduces boredom by 0.1 |
| Gluttony | Hunger below 0.2 continuously for one hour |
| Starvation | Hunger above 4.7 continuously for one hour |
| Overexcitement | Boredom below 0.2: immediate death |
| Extreme boredom | Boredom above 4.7: immediate death |
| Hypothermia | Water below 14°C continuously for 30 minutes |
| Hyperthermia | Water above 28°C continuously for 30 minutes |
| Transformation | After seven days of survival, the minnow becomes a golden sea snake |

The exact thresholds are strict: values equal to 0.2 or 4.7 are safe. Food dropped behind the creature takes three seconds to be noticed; uneaten food sinks and disappears.

AirCon cools at 1°C per 30 minutes; the heater warms at 1.5°C per 30 minutes. With both off, the tank approaches its natural temperature target at 0.2°C per five minutes. The natural target depends on the outdoor temperature: above 30°C, subtract 6°C; above 22°C through 30°C, subtract 3°C; from 16°C through 22°C, use outdoor temperature; from 8°C to below 16°C, add 3°C; below 8°C, add 6°C.

### Weather, storage and language

City search and outdoor temperature use [Open-Meteo](https://open-meteo.com/) when online. If weather cannot be retrieved, use the manual outdoor-temperature control. Daylight changes with the sun's position at the selected city; the default is Sha Tin, Hong Kong.

Your creature continues ageing in real time while the page is closed. Progress is saved automatically using browser **localStorage**. Changing the language **does not** create or reset a separate game save. The language choice is also remembered. Different browsers, devices or website origins do not share the save automatically. Clearing site data or using private browsing may erase it.

To publish: in **Settings → Pages**, select **Deploy from a branch**, branch **main**, and folder **/(root)**. The site runs directly from `index.html`.

---

## 繁體中文

### 遊戲玩法

本遊戲改編自 ESP32 CYD 水族箱，適合在 iPhone 的 Brave、Safari，以及電腦瀏覽器遊玩。頁面頂部設有 **繁體中文 / English** 語言切換按鈕，遊戲進行期間可隨時更改語言，毋須重新載入頁面或重新養魚。

- **輕觸水面：** 為金色小魚投下一粒飼料。小魚存活七天後，會變成金色海蛇，屆時改以小活魚餵食。
- **在水族箱內滑動：** 與魚兒玩耍，或令牠受驚游開。
- **冷氣：** 降低水溫；**暖水器：** 提高水溫。兩者不可同時運作，再次按下已啟動的按鈕即可關閉。
- **燈光：** 開關照明燈，每次有效切換均計作一次玩耍。關燈後，水族箱會按照所選城市的晝夜變化調節亮度。
- **設定：** 搜尋城市、取得即時天氣、手動設定戶外氣溫，以及閱讀飼養規則。
- **魚兒死亡後：** 按住水族箱底部的「新魚」區域兩秒，即可重新開始。

### 飼養與生存規則

| 情況 | 規則 |
| --- | --- |
| 初始數值 | 飢餓 2.5、無聊 2.5、年齡為零 |
| 自然變化 | 飢餓及無聊指數每 20 分鐘增加 0.1 |
| 吃下食物 | 飢餓指數下降 0.1 |
| 滑動或有效開關燈光 | 無聊指數下降 0.1 |
| 過度進食 | 飢餓指數連續一小時低於 0.2 |
| 飢餓死亡 | 飢餓指數連續一小時高於 4.7 |
| 過度興奮 | 無聊指數低於 0.2，立即死亡 |
| 極度無聊 | 無聊指數高於 4.7，立即死亡 |
| 失溫 | 水溫連續 30 分鐘低於 14°C |
| 高溫 | 水溫連續 30 分鐘高於 28°C |
| 進化 | 小魚存活滿七天後變成金色海蛇 |

**注意：** 指數剛好等於 0.2 或 4.7 時仍然安全。投在魚兒身後的食物須三秒後才會被察覺；未被吃掉的食物會下沉並消失。

冷氣每 30 分鐘降溫 1°C，暖水器每 30 分鐘升溫 1.5°C。兩者關閉時，水溫每五分鐘以 0.2°C 的速度接近自然目標水溫。自然目標水溫依戶外氣溫而定：高於 30°C 則減 6°C；高於 22°C 至 30°C 則減 3°C；16°C 至 22°C 與戶外相同；8°C 至低於 16°C 則加 3°C；低於 8°C 則加 6°C。

### 天氣、存檔與語言設定

遊戲預設城市為**香港沙田**，可於設定中搜尋其他城市。連線時透過 [Open-Meteo](https://open-meteo.com/) 取得天氣；未能取得時，可自行設定戶外氣溫。自然光暗按所選城市的太陽位置調節。

魚兒按**現實時間**成長，即使關閉瀏覽器，飢餓、無聊與水溫仍會繼續變化。遊戲以瀏覽器 **localStorage** 自動儲存進度。切換中英文只會改變顯示語言，**不會重設或另外建立魚兒存檔**；語言偏好也會保存。不同瀏覽器、裝置或網站來源的存檔不會自動同步。清除網站資料或使用私密瀏覽可能令進度遺失。

GitHub Pages 發佈方法：在儲存庫的 **Settings → Pages** 選擇 **Deploy from a branch**，分支選 **main**，資料夾選 **/(root)**，然後按 **Save**。首頁由 `index.html` 提供。

---

## Files / 檔案

- `index.html` — English and Traditional Chinese game, with live language switching / 可即時切換英語及繁體中文的遊戲
- `README.md` — Bilingual documentation / 中英雙語說明

This is a browser adaptation, not the original ESP32 firmware. The source game remains in [CYD-Aquarium](https://github.com/littlehohk/CYD-Aquarium). Physical iPhone testing has not yet been completed.

本版本為瀏覽器改編版，並非原有 ESP32 韌體；尚未在實體 iPhone 上完成全面測試。
