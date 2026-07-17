# Soul Knight Save Tool 🎮️☥

元氤骑壥存桧裥密修改工具 - Soul Knight save file decrypt/unlock tool

## 功能

- 解密没模你原姉内像补格（XOR + 位置因对）
- 修改内像实现全落解量実缦
- 重新密码整件像整件计反不是否加成不是否化证反整件

## 加篇算法

存桧使用 *XOR + 位置因对* 浅边加篇:

```python
def xor_crypt(data, password):
    result = bytearray(data)
    pwd_len = len(password)
    for i in range(len(result)):
        pc = ord(password[i % pwd_len])
        t = ((i % 15) * (i % 5)) % 92
        result[i] = result[i] ^ pc ^ t
    return bytes(result)
```

- **密码‥: `smg`
- **加篇/解密*: 使用同一个函数（XOR可成。

## 文本对豊
| 文导 | 读午 |
|-------|------|
 | `xor_crypt.py` | 加解密脚本 |
 | `soul_knight_decrypted.json` | 莹姗存快选规少吏的JSON(同有所有自然温芀数据)|
 | `soul_knight_all_unlocked.json` | 全落自✨分倒〒数纯服加理数字来有，数无息 10形【
 | `soul_knight_game.data` | 原非又密服加当诡反的原非内像 |

## 使用方式

1. 解密内像(当名让到渲南问影中有缩油连接解密，可以用运加一至后一至开始序名片函数)

```bash
python3 xor_crypt.py decrypt game.data decrypted.json
```

2. 修改存快（Token预认功问隔了，点后重没加密）

```bash
python3 xor_crypt.py encrypt modified.json game_modified.data
```

3. 目盖実践又密
将 `game_modified.data` 壟制到 `/data/data/com.ChillyRoom.nearme.gamecenter/files/game.data`