# 馃摜 鎶€鑳藉畨瑁呮寚鍗?
鏈枃妗ｈ缁嗚鏄庡浣曞畨瑁?OpenClaw 鎶€鑳姐€?
---

## 鍓嶇疆鏉′欢

- 鉁?宸插畨瑁?OpenClaw
- 鉁?鏈?GitHub 璐﹀彿
- 鉁?鐔熸倝鍩烘湰鍛戒护琛屾搷浣?
---

## 鏂规硶涓€锛欸it Clone锛堟帹鑽愶級

### Windows

```powershell
# 1. Clone 浠撳簱
git clone https://github.com/starxxy/openclaw-skills.git

# 2. 澶嶅埗鎶€鑳芥枃浠?xcopy /E /I openclaw-skills\skills %USERPROFILE%\.openclaw\skills\

# 3. 楠岃瘉瀹夎
dir %USERPROFILE%\.openclaw\skills\
```

### macOS/Linux

```bash
# 1. Clone 浠撳簱
git clone https://github.com/starxxy/openclaw-skills.git

# 2. 澶嶅埗鎶€鑳芥枃浠?cp -r openclaw-skills/skills ~/.openclaw/skills/

# 3. 楠岃瘉瀹夎
ls ~/.openclaw/skills/
```

---

## 鏂规硶浜岋細鎵嬪姩涓嬭浇

1. 璁块棶浠撳簱锛歨ttps://github.com/starxxy/openclaw-skills
2. 鐐瑰嚮 "Code" 鈫?"Download ZIP"
3. 瑙ｅ帇 ZIP 鏂囦欢
4. 澶嶅埗 `skills/` 鐩綍鍒?`~/.openclaw/skills/`

---

## 鏂规硶涓夛細鍗曚釜鎶€鑳藉畨瑁?
濡傛灉鍙渶瑕佹煇涓妧鑳斤細

```bash
# 绀轰緥锛氬彧瀹夎 feishu-doc 鎶€鑳?mkdir -p ~/.openclaw/skills/feishu-doc
curl -o ~/.openclaw/skills/feishu-doc/SKILL.md \
  https://raw.githubusercontent.com/starxxy/openclaw-skills/main/skills/feishu-doc/SKILL.md
```

---

## 楠岃瘉瀹夎

### 1. 妫€鏌ョ洰褰曠粨鏋?
```bash
# 搴旇鐪嬪埌锛?# ~/.openclaw/skills/feishu-doc/SKILL.md
# ~/.openclaw/skills/feishu-wiki/SKILL.md
# 绛?..
```

### 2. 閲嶅惎 OpenClaw

鍏抽棴骞堕噸鏂版墦寮€ OpenClaw锛岃鎶€鑳界敓鏁堛€?
### 3. 娴嬭瘯鎶€鑳?
鍦?OpenClaw 涓皾璇曪細

```
鍒涘缓涓€涓涔︽枃妗ｏ紝鏍囬鏄?娴嬭瘯"
```

濡傛灉鎶€鑳芥甯稿伐浣滐紝浼氳嚜鍔ㄦ縺娲?feishu-doc銆?
---

## 甯歌闂

### Q1: 鎶€鑳戒笉鐢熸晥锛?
**瑙ｅ喅**锛?1. 妫€鏌ユ枃浠惰矾寰勬槸鍚︽纭?2. 纭 SKILL.md 鏍煎紡姝ｇ‘
3. 閲嶅惎 OpenClaw

### Q2: 鏉冮檺閿欒锛?
**瑙ｅ喅**锛?```bash
# macOS/Linux 淇鏉冮檺
chmod -R 755 ~/.openclaw/skills/
```

### Q3: 鎶€鑳藉啿绐侊紵

**瑙ｅ喅**锛?1. 妫€鏌ユ槸鍚︽湁閲嶅鐨勬妧鑳藉悕绉?2. 鏌ョ湅 OpenClaw 鏃ュ織
3. 鏆傛椂绂佺敤鍐茬獊鎶€鑳?
---

## 鍗歌浇鎶€鑳?
```bash
# 鍒犻櫎鐗瑰畾鎶€鑳?rm -rf ~/.openclaw/skills/feishu-doc/

# 鍒犻櫎鎵€鏈夋妧鑳斤紙璋ㄦ厧锛侊級
rm -rf ~/.openclaw/skills/
```

---

**鏈€鍚庢洿鏂?*锛?026-03-14