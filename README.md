# kft-cowork-update

[KFT Cowork](https://github.com/5minlab/kft-cowork) 앱이 참조하는 **공개 업데이트 채널**입니다. `main` 브랜치의 파일만 사용합니다.

## 파일

| 파일 | 설명 |
|------|------|
| **`VERSION`** | 한 줄, 시맨틱 버전 (예: `0.2.5`). 앱의 `app.getVersion()`보다 크면 “새 버전 있음”으로 처리합니다. |
| **`update-manifest.json`** | 선택. 플랫폼별 설치 파일 **HTTPS URL**과 릴리스 페이지 링크. |

원시(raw) URL 예:

- `https://raw.githubusercontent.com/5minlab/kft-cowork-update/main/VERSION`
- `https://raw.githubusercontent.com/5minlab/kft-cowork-update/main/update-manifest.json`

## 배포 절차

1. **GitHub Releases**에 `dmg` / `exe` / `AppImage` 등 아티팩트를 올립니다.
2. **`VERSION`**을 새 버전 한 줄로 수정해 커밋합니다.
3. **`update-manifest.json`**의 `version`을 맞추고, `downloads`에 OS별 URL을 채웁니다.  
   - URL이 없으면 앱은 **릴리스 페이지 열기**만 안내합니다 (`releasePageUrl`).
4. `main`에 푸시하면 앱이 다음 확인 시 새 버전을 봅니다.

### `update-manifest.json` 예시 (URL 채운 뒤)

```json
{
  "version": "0.2.5",
  "releasePageUrl": "https://github.com/5minlab/kft-cowork-update/releases",
  "releaseNotesUrl": "https://github.com/5minlab/kft-cowork-update/releases/tag/v0.2.5",
  "downloads": {
    "darwin": {
      "universal": "https://github.com/5minlab/kft-cowork-update/releases/download/v0.2.5/KFT-Cowork-0.2.5.dmg"
    },
    "win32": {
      "x64": "https://github.com/5minlab/kft-cowork-update/releases/download/v0.2.5/KFT-Cowork-Setup-0.2.5.exe"
    },
    "linux": {
      "x64": "https://github.com/5minlab/kft-cowork-update/releases/download/v0.2.5/KFT-Cowork-0.2.5.AppImage"
    }
  }
}
```

앱 쪽 상세 스펙은 kft-cowork 저장소의 **`docs/UPDATE_CHANNEL.md`**를 참고하세요.
