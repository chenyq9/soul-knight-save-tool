# Soul Knight Save Tool 🎮⚔️

元气骑士（Soul Knight）存档解密/修改工具

## 功能

- 解密元气骑士游戏存档（XOR + 位置因子加密）
- 修改存档实现全英雄解锁、满级
- 重新加密存档文件并保持与原始文件大小一致

## 加密算法

存档使用 **XOR + 位置因子** 混合加密：

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

- **密码**: `smg`
- **加密/解密**: 使用同一个函数（XOR可逆）

## 文件说明

| 文件 | 说明 |
|------|------|
| `xor_crypt.py` | 加解密脚本 |
| `soul_knight_decrypted.json` | 原始存档解密后的JSON（含所有英雄皮肤数据） |
| `soul_knight_all_unlocked.json` | 全英雄解锁 + 满级 + 金币修改版本 |

## 使用方法

### 1. 解密存档
```bash
python3 xor_crypt.py decrypt game.data decrypted.json
```

### 2. 修改存档（编辑JSON，然后重新加密）
```bash
python3 xor_crypt.py encrypt modified.json game_modified.data
```

### 3. 覆盖游戏存档
将 `game_modified.data` 复制到 `/data/data/com.ChillyRoom.nearme.gamecenter/files/game.data`
