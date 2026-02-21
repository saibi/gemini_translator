# 출처 및 번역 정보
- **원문 URL:** https://dev.to/samyc2002/neovim-for-beginners-4g2d
- **번역:** Cursor AI (기술 문서 번역)

---

# 초보자를 위한 Neovim

약 22분 읽기 · 2024년 9월 30일

![cover](https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fuddtj2l9nh7mj6lzvtgb.png)

(이미지 링크: `https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fuddtj2l9nh7mj6lzvtgb.png`)

이런 사정이 있어요. 저는 원래 일주일에 글 하나씩 쓰려고 했는데, 여러 이유로 원래 쓰려던 주제에 대해 충분히 조사할 시간이 없었습니다. 잘 모르는 주제로 어설프게 글을 쓰느니, 그보단 제가 그래도 좀 아는 걸 쓰는 게 낫겠다 싶었고요. 그래서 이번에는 **Neovim** 이야기를 하려고 합니다. 예전에 쓰던 텍스트 에디터인데, “이제 다시는 안 쓸 것 같다”라고 생각했던 순간이 와도 결국 다시 돌아오게 되더라고요.

## 제 Neovim 여정

본론으로 들어가기 전에, 먼저 제 Neovim 여정부터 공유해볼게요. Neovim을 처음 쓰기 시작한 건 3년 전쯤이에요. 그때는 대학 2학년이었고 Linux를 배우고 있었습니다. 하드웨어/소프트웨어 이슈가 겹쳐서 VS Code가 제대로 안 돌아가는 바람에 Sublime Text(개인적으로 정말 좋은 도구라고 생각해요)를 써야 했죠.

하지만 저는 Sublime을 쓰면서도 뭔가 만족이 안 됐어요. “이건 아닌데…” 싶은 느낌이 들어서 다른 에디터를 찾아보기 시작했고, 그 과정에서 Brackets, Atom, Eclipse도 써봤지만 제 취향엔 맞지 않았습니다. 그러다 **vim**을 알게 됐어요(네, Neovim이 아니라 vim이요).

### 처음의 한 걸음

vim을 쓰기 시작하면서 단축키와 키바인딩을 익혔고, 결국엔 설정 파일도 만들었죠(`init.vim.....Ah.....` 이거 진짜 추억이네요). 꽤 만족스럽긴 했는데, 그래도 뭔가 하나가 빠진 느낌이 계속 들었습니다.

그때 저는 **Primeagen**을 보기 시작했고, 영상 중 하나에서 Neovim 이야기를 들었어요. 궁금해서 찾아봤죠. “vim의 포크(fork)고, 네이티브 LSP 지원 같은 추가 기능도 많다” 정도는 들었지만, 처음엔 저한테는 거의 똑같아 보였고 크게 와닿진 않았습니다. 그런데 어느 순간, 상황이 바뀌는 계기가 있었어요.

### Linux 라이싱(ricing)의 세계

앞서 말했듯 저는 Linux를 배우고 있었고, 당연하게도 Linux 라이싱(ricing) 문화도 곧 접하게 됐습니다. 당시에는 HP Pavilion 노트북에 Ubuntu를 설치해 쓰고 있었는데, 기본 GNOME 룩이 너무 심심했어요. 플러그인이나 이것저것으로 커스터마이징을 시도했지만 그때는 마음에 들지 않았습니다.

그러다 **Distrotube** 채널을 알게 되면서 Linux 라이싱을 배우기 시작했고, 여러 윈도 매니저/바/런처를 설치하면서 설정 파일을 잔뜩 만지기 시작했어요. 제가 처음 쓴 윈도 매니저 중 하나가 **awesome window manager**였는데, 이게 Lua로 설정하거든요. Neovim 설정에도 Lua를 쓰니까, 그때 제대로 Lua를 익히게 됐습니다.

그런데 데스크톱만 예쁘게 만드는 걸로는 만족이 안 됐어요. 에디터도 테마에 맞춰야 했거든요. 그래서 **LunarVim**을 쓰기 시작했습니다.

### 첫 Neovim 배포판(distro)

모르는 분을 위해 설명하자면, LunarVim은 Neovim “배포판(distro)” 같은 겁니다. [@chrisatmachine](https://www.youtube.com/@chrisatmachine)이 만든 특정 설정 세트라고 보면 돼요. 제가 처음 봤을 때는 아직 초기 단계라서 추상화가 많지 않았고, 설정을 거의 그대로 볼 수 있었습니다.

저는 성격상 그걸 파고들었고, 한 달쯤 지나니 대략 어떻게 돌아가는지 감이 잡혔습니다. 그러고 나서 제 첫 “커스텀 설정”을 만들었고, 그걸 메인으로 쓰기 시작했죠.

### 나만의 악마 만들기

> _We create our own demons_  
> - Tony Stark

커스텀 설정을 만들고 나서 매일 쓰기 시작했는데, 오히려 생산성이 올라가기는커녕 내려가고 있다는 걸 느꼈습니다. 이유는 간단했어요. 저는 계속 설정을 고치고 있었거든요.

일을 시작할 때마다 뭔가 문제가 보였고, 그러면 설정을 만지작거리기 시작해서 거기에 시간을 많이 썼습니다. 이런 습관은 Neovim에만 해당하진 않았어요. 윈도 매니저 설정, polybar 설정, rofi 설정도 가끔 바꾸긴 했지만, Neovim은 훨씬 자주 쓰다 보니(당시엔 제가 초보였고 지금도 그렇습니다 xD) 더 많은 문제가 눈에 들어왔고 그때마다 고치게 되더라고요. 그러다 보니 하루 시간을 많이 잃었고, 결국 일/공부에도 영향을 주기 시작했어요. 그래서 저는 **NvChad**로 옮겼습니다.

### Chad 설정

NvChad는 제가 원하던 “꿈의 셋업”이었어요. VS Code처럼 보이지만 vim 안에서 돌아가니까 너무 좋았습니다. 그렇게 가장 오래(대략 5~6개월) 메인으로 썼죠.

역시나 저는 코드도 들여다보면서 “이건 어떻게 동작하지?”를 계속 파고들었고, 바꿔 보기도 하면서 셋업이 어떻게 달라지는지 확인했습니다. 그 6개월 동안 Neovim에 대해 가장 많이 배웠어요. 버퍼(buffers), 윈도(windows), 탭(tabs), 그리고 이들의 차이를 이해했고, 키바인딩이 실제로 어떻게 동작하는지도 알게 됐습니다(그전엔 거의 복붙이라서, 제대로 이해를 못 했거든요). Neovim 자동 명령(autocommands) 같은 것들도 배우면서요.

그리고 여기서 하나 더 배운 게 있는데, 그게 바로 이 글의 핵심이기도 합니다. “실제로 쓸만한 셋업”에 뭐가 필요한지 알게 됐거든요.

### 처음부터 설정 작성하기

네, 또 설정을 만들었습니다(어떻게 했는지 모르겠는데 그 설정 코드를 통째로 잃어버리기도 했어요 😅). 그런데 이번엔 생산성이 확 올라가더라고요. “Samy, NvChad를 좋아했다면서 왜 굳이 또 직접 만들었어요?”라고 묻고 싶을 텐데요. 제 답은 이렇습니다.

- Neovim은 개인화된 에디터라고 생각해서, 제 필요에 맞는(미니멀하고, 빠르고, 안정적인) 구성이 필요했습니다. 그래서 커스텀 설정을 만들었고, Linux를 쓰는 동안은 계속 그 설정을 썼어요. 지금은 Windows를 쓰고 있고, 또 다른 설정을 쓰는 중입니다.
- NvChad는 VS Code와 너무 비슷했고, 제가 안 쓰는 것들도 잔뜩 들어 있어서(= bloated) 부담이 있었어요. 게다가 VS Code가 떠올라서인지, 어느 순간엔 집중이 잘 안 되더라고요(좀 애매한 이유긴 합니다).

### 내 노트북을 새로 장만하다

“잠깐, 노트북 있다면서요!”라고 생각하는 분도 있겠죠. 맞아요. 노트북은 있었는데, 돈을 모아서 게이밍 노트북을 샀습니다(기존 노트북은 사무용에 가까워서 게임이 잘 안 돌아갔거든요). 저는 게임을 좋아하기도 하고요.

문제는… 게이밍하려면 Windows를 써야 했습니다. Linux 게임 환경이 별로였거든요(지금도 그렇다고 생각하지만, 그건 또 다른 이야기). 새 노트북은 좋았는데 Windows는 싫어서 2~3개월은 계속 욕했던 것 같아요. Linux에서 쓰던 도구들이 Windows에는 없는 게 많았거든요.

그러다 어느 순간 “필요하면 내가 만들면 되지”라는 생각이 들었고, Neovim도 설치해서 새 셋업을 구성했습니다. 관심 있으면 댓글로 알려주세요. Windows에서 Linux 셋업(혹은 그에 가까운 것)을 되살리기 위해 제가 했던 것들도 공유해볼게요.

## Neovim 설정의 기본 구성 요소

배경 이야기는 이쯤이면 충분하겠죠. 이제 본론으로 들어가 볼게요. 기본 셋업을 만들려면 아래가 필요합니다.

1. 터미널과 Neovim 설치(당연하지만요)
2. 괜찮은 기본 설정들(아래에서 설명)
3. 괜찮은 키바인딩(아래에서 설명)
4. Treesitter
5. 퍼지 파인더(fuzzy finder) (예: Telescope)
6. 필요한 플러그인들(사용자에 따라 다르지만, 아래에 제가 쓰는 플러그인과 필수급 플러그인을 공유할게요)

보시다시피 컬러스킴(colorscheme)과 파일 트리(file tree)는 일부러 뺐습니다. 제 생각엔 퍼지 파인더가 있으면 파일 트리는 그렇게 중요하지 않거든요. 물론 원하면 써도 됩니다(저도 결국은 하나를 쓰고 있고, 6번에 포함해뒀어요).

이제 각 항목을 어떻게 설정하는지 하나씩 보겠습니다. 저는 제가 어떻게 구성했는지 설명하고, 각각의 문서(documentation)도 연결해둘게요. 자세한 내용은 문서를 읽는 걸 강력히 추천합니다. 이 글은 “표면을 훑어서” 쉽게 이해하도록 돕는 게 목적이지만, 실제로 동작 원리까지 이해하려면 문서를 보는 게 필수예요.

### 터미널과 Neovim 설치

이건 말 그대로 기본이죠. Neovim은 터미널 텍스트 에디터이기 때문에 터미널이 필수입니다. Neovim을 GUI 앱으로 띄우는 방법도 있고, 원하면 그렇게 써도 됩니다.

다만 제 경험상 GUI는 (제 경우에는) 파일을 많이 열고 플러그인이 많아지면 느려지거나, 어떤 설정이 비활성화되는 경우가 있었습니다(예: 투명 배경이 갑자기 비활성화되는 등).

지금 제 Windows 워크플로에서 선택한 터미널은 OG **Windows Terminal**입니다. 약 6개월 정도 매일 Neovim을 여기서 쓰고 있는데 아직 큰 문제는 못 겪었어요. 물론 잘 동작하게 하려면 키바인딩을 좀 바꿔야 했습니다(예: Ctrl+V가 Neovim의 비주얼 블록 모드와 충돌해서, Windows Terminal에서 Ctrl+V를 껐어요).

Windows에서 Neovim을 세팅하려면, 먼저 Neovim을 설치합니다. 저는 winget을 썼어요.

```bash
$ winget install Neovim.Neovim
```

chocolatey나 scoop 같은 다른 패키지 매니저를 써도 됩니다. Neovim을 설치한 다음에는 설정을 `C:\Users\_username_\AppData\Local\nvim` 폴더에 작성하면 됩니다. 폴더가 없으면 만들면 되고요. 설정은 그 폴더의 `init.lua` 파일에 들어갑니다.

제가 쓰는 폴더 구조는 이렇습니다.

```
├───lua
│   ├───config
│   │   ├───comments.lua
│   │   ├───context.lua
│   │   ├───git.lua
│   │   ├───harpoon.lua
│   │   ├───illuminate.lua
│   │   ├───init.lua
│   │   ├───lazy.lua
│   │   ├───lsp.lua
│   │   ├───lualine.lua
│   │   ├───telescope.lua
│   │   ├───treesitter.lua
│   │   ├───trouble.lua
│   │   └───undotree.lua
│   └───samy
│   │   ├───autocommands.lua
│   │   ├───git.lua
│   │   ├───init.lua
│   │   ├───keybinds.lua
│   │   └───settings.lua
└───undodir
```

일단 지금은 파일이 많아도 신경 쓰지 마세요. 제가 세운 간단한 규칙은 이겁니다.

- 플러그인 설정은 `config/`에 둔다.
- 제가 직접 만든 설정은 `samy/`에 둔다.

이렇게 하면 코드가 깔끔해지는 데 도움이 됩니다(…완벽히 깔끔하진 않지만요 😅).

### 괜찮은 기본 설정들

이건 이해하기 쉽게 몇 개 하위 섹션으로 나눠서 설명하겠습니다.

#### 줄 번호

Neovim의 줄 번호는 보통 3가지 방식이 있습니다.

1. 줄 번호 없음(기본값)
   ![no-line-numbers-demo](https://res.cloudinary.com/dxioyklts/image/upload/v1727686390/Screenshot_2024-09-29_232036_hnxtjd.png)
   (이미지 링크: `https://res.cloudinary.com/dxioyklts/image/upload/v1727686390/Screenshot_2024-09-29_232036_hnxtjd.png`)
2. 일반 줄 번호
   ![regular-line-numbers-demo](https://res.cloudinary.com/dxioyklts/image/upload/v1727686390/Screenshot_2024-09-29_232120_so6vgw.png)
   (이미지 링크: `https://res.cloudinary.com/dxioyklts/image/upload/v1727686390/Screenshot_2024-09-29_232120_so6vgw.png`)
3. 상대 줄 번호
   ![relative-line-numbers-demo](https://res.cloudinary.com/dxioyklts/image/upload/v1727686391/Screenshot_2024-09-29_232152_qnylam.png)
   (이미지 링크: `https://res.cloudinary.com/dxioyklts/image/upload/v1727686391/Screenshot_2024-09-29_232152_qnylam.png`)

저는 개인적으로 일반 줄 번호 + 상대 줄 번호를 섞어 씁니다. 설정은 이렇게 해요.

```lua
local opts = vim.opt

-- 줄 번호
opts.nu = true
opts.relativenumber = true
```

그리고 이렇게 보입니다.

![mixed-line-numbers-demo](https://res.cloudinary.com/dxioyklts/image/upload/v1727686391/Screenshot_2024-09-29_232335_fr2bff.png)

(이미지 링크: `https://res.cloudinary.com/dxioyklts/image/upload/v1727686391/Screenshot_2024-09-29_232335_fr2bff.png`)

현재 줄의 “실제 줄 번호”는 그대로 보이면서, 나머지는 활성 줄을 기준으로 상대 숫자로 표시되는 게 보이죠. 이게 파일 안에서 코드 이동할 때 꽤 도움이 됩니다.

예를 들어 “General settings” 파트로 가고 싶다고 해볼게요. `j`를 여러 번 누르는 대신, `13j`처럼 “숫자 + j”로 한 번에 내려갈 수 있습니다. 상대 줄 번호가 `13`으로 보이니까, `25j`인지 `6j`인지 헷갈리지 않고요.

#### 들여쓰기

들여쓰기는 설명이 필요 없죠. 솔직히 들여쓰기 잘 된 코드는 좀 멋있습니다(농담이에요. 저는 제 코드 들여쓰기에 설레진 않습니다). 저는 개인적으로 4칸 들여쓰기를 좋아하는데, 로직을 모듈화해야 할 타이밍이나 나쁜 코드 냄새를 더 빨리 발견하는 데 도움이 되더라고요(진짜예요. 4칸 들여쓰기는 나쁜 코드를 더 잘 드러냅니다).

제가 쓰는 들여쓰기 설정은 이렇습니다.

```lua
-- 들여쓰기
opts.tabstop = 4
opts.softtabstop = 4
opts.shiftwidth = 4
opts.expandtab = true
opts.smartindent = true
```

#### 검색과 기타 일반 설정

이 섹션은 제가 개인적으로 선호하는 설정들입니다. 동의하지 않을 수도 있고, 그건 전혀 문제 없어요. 취향에 맞게 바꾸시면 됩니다.

저는 줄바꿈(wrap)을 끄고 쓰는 편이라서 이렇게 둡니다.

```lua
-- 일반 설정
opts.wrap = false
```

swapfile은 끄는 걸 좋아합니다. 이걸 끄면 비정상 종료 같은 상황에서 버퍼가 저장되는 동작을 하지 않게 됩니다. 그래서 이렇게 둬요.

```lua
opts.swapfile = false
opts.backup = false
```

다음 두 줄은 undotree라는 플러그인과 관련이 있는데, 저는 이 플러그인도 추천합니다(아래에서 더 설명할게요).

```lua
opts.undodir = "C:\\Users\\samy3\\AppData\\Local\\nvim\\undodir"
opts.undofile = true
```

현재 줄을 하이라이트하는 것도 좋아해서 이렇게 켭니다.

```lua
opts.cursorline = true
```

아래 두 줄은 검색 하이라이트와 증분 검색(incremental search)을 설정합니다.

```lua
-- 검색
opts.hlsearch = false
opts.incsearch = true
```

`hlsearch = false`는 “검색이 끝난 뒤에도 계속 하이라이트”되는 걸 막습니다. 저는 그게 좀 이상해 보여서 꺼둬요. 한 번 켜보고 마음에 들면 켜도 됩니다.

`incsearch = true`는 검색이 진행되는 동안 실시간으로 하이라이트해 줍니다. 예를 들어 `/`를 누르고 `sea`를 입력하면, `sea`가 들어간 모든 부분이 즉시 하이라이트됩니다. 이게 기본값이 아니라서 켜줘야 한다는 걸 처음 알았을 때 저도 좀 놀랐습니다.

### 괜찮은 키바인딩

키바인딩과 단축키는 완전히 취향 영역이라서, 여기서는 제가 쓰는 것과 커스터마이징 팁 정도만 공유할게요. 제가 쓰는 키바인딩은 아래와 같습니다.

```lua
vim.g.mapleader = " "

local keymap = vim.keymap

-- keymap.set("n", "<leader>pv", vim.cmd.Ex)

-- VS Code 스타일 줄 이동
keymap.set("v", "J", ":m '>=1<CR>gv=gv")
keymap.set("v", "K", ":m '<-2<CR>gv=gv")

-- 삶을 편하게 하는 키바인딩
keymap.set("i", "jj", "<Esc>")
keymap.set("n", "Y", "yg$")
keymap.set("n", "J", "mzJ`z")
keymap.set("n", "<C-d>", "<C-d>zz")
keymap.set("n", "<C-u>", "<C-u>zz")
keymap.set("n", "n", "nzzzv")
keymap.set("n", "N", "Nzzzv")

-- 여러 유틸리티용 복사/붙여넣기 키바인딩
keymap.set("x", "<leader>p", "\"_dP")
keymap.set("n", "<leader>y", "\"+y")
keymap.set("v", "<leader>y", "\"+y")
keymap.set("n", "<leader>Y", "\"+Y")
keymap.set("n", "<leader>d", "\"_d")
keymap.set("v", "<leader>d", "\"_d")

-- 더 삶의 질을 올려주는 키바인딩
keymap.set("n", "Q", "<nop>")
keymap.set("n", "<leader>f", function ()
    vim.lsp.buf.format({ async = true })
end)
keymap.set("n", "<leader>x", "<cmd>!chmod +x %<CR>", { silent = true })

-- 오류 탐색
keymap.set("n", "<C-k>", "<cmd>cprev<CR>", { silent = true })
keymap.set("n", "<C-j>", "<cmd>cnext<CR>", { silent = true })

-- 버퍼 탐색
keymap.set("n", "<leader>bx", "<cmd>bdelete<CR>", { silent = true })
keymap.set("n", "<leader>bb", "<cmd>bnext<CR>", { silent = true })
keymap.set("n", "<leader>bB", "<cmd>bprev<CR>", { silent = true })
```

**Disclaimer:** 이 중 일부는 Primeagen 설정에서 가져온 것이라, Primeagen을 보시는 분이라면 익숙해 보일 수 있어요.

이게 뭘 하는지 간단히 풀면 이렇습니다.

1. `vim.g.mapleader`는 리더 키(leader key)를 설정합니다. Neovim에서 “모드 키(mod key)” 같은 개념이라고 보면 돼요. SUPER, META, ALT, CTRL, SHIFT도 쓸 수는 있지만, 리더 키로 지정하는 건 보통 좋은 생각이 아닙니다. 많은 분들이 SPACE를 리더 키로 쓰고, 저도 그렇습니다.
2. `keymap.set`은 키바인딩을 설정합니다. 모드, 바인딩할 키(혹은 키스트로크), 그리고 연결할 키/함수/명령을 지정하면 됩니다. `n`은 Normal 모드, `i`는 Insert 모드, `v`나 `x`는 비주얼 계열 모드, `t`는 터미널 모드에 씁니다.

이 키바인딩을 그대로 쓰고 싶다면, 결과적으로 이런 동작들을 갖게 됩니다.

| 모드 | 키 | 동작 |
| --- | --- | --- |
| Normal | Y | 현재 줄에서 끝까지 yank |
| Normal | J | 현재 줄과 다음 줄을 합치고 커서는 마지막 줄에 유지 |
| Normal | Ctrl + d | 반 페이지 아래로 스크롤하고 커서를 화면 중앙에 유지 |
| Normal | Ctrl + u | 반 페이지 위로 스크롤하고 커서를 화면 중앙에 유지 |
| Normal | n | 다음 검색 결과로 이동 |
| Normal | N | 이전 검색 결과로 이동 |
| Normal | Leader + y | 클립보드에 복사 |
| Normal | Leader + y | 한 줄 전체를 클립보드에 복사 |
| Normal | Leader + d | yank 버퍼에 남기지 않고 삭제 |
| Normal | Leader + f | 활성 LSP로 문서 포맷 |
| Normal | Leader + x | 현재 스크립트를 실행 가능하게 만들기(Linux에서만 동작) |
| Normal | Ctrl + j | 다음 오류로 이동 |
| Normal | Ctrl + k | 이전 오류로 이동 |
| Normal | Ctrl + bx | 버퍼 닫기 |
| Normal | Ctrl + bb | 다음 버퍼로 이동 |
| Normal | Ctrl + bB | 이전 버퍼로 이동 |
| Insert | jj | Insert 모드 종료 |
| Visual | J | 선택한 줄을 아래로 이동 |
| Visual | K | 선택한 줄을 위로 이동 |
| Visual | Leader + y | 선택 영역을 클립보드에 복사 |
| Visual | Leader + d | 선택 영역을 yank 버퍼에 남기지 않고 삭제 |
| Visual | Leader + x | 선택을 복사하지 않고 붙여넣기 |

### Treesitter

Treesitter는 Neovim을 “컬러풀”하게 만들어주는 핵심입니다. LSP와 컬러스킴(colorscheme) 등을 활용해서 변수, 키워드 같은 것들을 하이라이트해 줍니다. Treesitter가 어떻게 동작하는지, 그리고 어떻게 설정해야 하는지는 [문서](https://github.com/nvim-treesitter/nvim-treesitter/wiki)를 참고하세요. 아래는 제 Treesitter 설정입니다.

```lua
require('nvim-treesitter.install').prefer_git = true
require 'nvim-treesitter.configs'.setup {
    ensure_installed = { 'bash', 'c', 'diff', 'html', 'lua', 'luadoc', 'markdown', 'vim', 'vimdoc', 'javascript', 'rust', 'typescript', "comment" },
    -- 설치되지 않은 언어 자동 설치
    auto_install = true,
    highlight = {
        enable = true,
        -- 일부 언어는 들여쓰기 규칙 때문에 Vim의 정규식 하이라이트 시스템(예: Ruby)에 의존합니다.
        -- 들여쓰기가 이상하게 동작한다면, 해당 언어를
        -- additional_vim_regex_highlighting 목록에 추가하고(또는) indent 비활성화 목록에 넣어보세요.
        additional_vim_regex_highlighting = { 'ruby' },
    },
    indent = { enable = true, disable = { 'ruby' } },
}
```

### 퍼지 파인더(fuzzy finder)

저는 퍼지 파인더로 Telescope를 씁니다. Telescope [문서](https://github.com/nvim-telescope/telescope.nvim/wiki)는 여기 있고, 제 설정은 아래와 같습니다.

```lua
local builtin = require("telescope.builtin")

local keymap = vim.keymap

keymap.set("n", "<leader>pf", builtin.find_files, {})
keymap.set("n", "<leader>bl", builtin.buffers, {})
keymap.set("n", "<leader>pp", builtin.git_files, {})
keymap.set("n", "<leader>ps", function ()
	builtin.grep_string({ search = vim.fn.input("Search: ") });
end)
```

이게 무슨 뜻인지 설명해볼게요.

Telescope 플러그인을 설치하고, Neovim 세션 시작 시점에 로드되면, `find_files`, `buffers`, `git_files` 같은 기능을 언제든 호출할 수 있습니다. 이런 기능을 실행하는 명령들도 있는데, 자세한 건 문서에 잘 정리돼 있어요. 여기서는 Lua 함수 호출로 실행하고 있습니다.

정리하면 `builtin`에 Telescope 패키지 안의 함수들이 들어 있고, 그중 필요한 함수를 호출하는 구조예요(Neovim 라이브러리 전반에 통하는 “상위 레벨” 설명이기도 합니다). 그리고 그 호출을 키바인딩으로 묶은 거죠.

| 모드 | 키 | 동작 |
| --- | --- | --- |
| Normal | Leader + pf | 모든 파일에서 검색(예: `node_modules`처럼 git ignore된 파일도 포함) |
| Normal | Leader + pp | git에 포함된 파일에서만 검색(git ignore된 파일은 제외) |
| Normal | Leader + bl | 활성 버퍼 목록(열려 있는 버퍼/파일 사이 이동) |
| Normal | Leader + ps | 프로젝트 전체에서 특정 문자열 검색(VS Code의 검색과 유사) |

여기까지 읽고 나면 두 가지가 헷갈릴 수 있어요.

1. 위에서 말한 Telescope나 Treesitter를 도대체 어떻게 설치하나요?
2. 버퍼(buffers)와 파일(files)은 어떻게 다른가요?

1번은 다음 섹션(필요한 플러그인들)에서 다루니 조금만 기다려 주세요. 2번은 지금 바로 이해해봅시다.

### 보너스: Neovim에서 파일(과 폴더) 열기

IDE나 메모장을 써 본 분이라면, 파일 여는 건 간단하죠. 파일을 클릭(혹은 더블클릭)하면 에디터에 열려서 편집하면 됩니다. 그런데 Neovim은 늘 그렇듯, 여기서도 한 단계 더 나아갑니다.

Neovim에서 파일을 여는 개념은 크게 3가지가 있어요.

1. 버퍼(Buffers)
2. 윈도와 패널(Window and Panes)
3. 탭(Tabs)

하나씩 보겠습니다. 먼저 윈도(window)부터요. 이해를 쉽게 하려고 VS Code를 예로 들어볼게요.

VS Code에서 파일을 열면 “탭”에 열립니다. 그리고 우리가 지금 쓰고 있는 VS Code 전체 창을 보통 “윈도(window)”라고 부르죠(저도 99.99% 확신합니다). Neovim도 마찬가지로, 세션을 시작하면 윈도 하나가 뜹니다.

VS Code에서 분할 보기(split view)를 써 본 적이 있다면, 윈도를 여러 패널(pane)로 나눌 수 있다는 것도 알 거예요. 이 경우 같은 파일을 다시(옆에) 열어서 side-by-side로 보는 느낌이죠.

Neovim에서도 패널(pane)과 윈도(window)는 비슷하게 동작합니다. **윈도(window)**는 Neovim 윈도이고, **패널(pane)**은 그 윈도를 분할한 것입니다(세로/가로 분할).

차이가 있다면 “내용을 보여주는 방식”이에요. Neovim은 파일을 실제로는 한 번만 열고, 그걸 옆에 나란히 보여줍니다. 이때 핵심이 **버퍼(buffer)**입니다. Neovim은 파일이나 폴더를 열면 항상 버퍼로 열고, 그 버퍼를 여러 패널에 보여줍니다. 같은 작업을 위해 메모리를 덜 쓰게 되는 거죠(이게 제가 VS Code를 예전만큼 못 쓰게 된 이유이기도 합니다).

정리해보면 이렇습니다. 파일에서 Enter를 치거나 어떤 방식으로든 파일을 열면, Neovim이 그 파일의 버퍼를 만들고 윈도에 보여줍니다. 윈도를 분할해서 패널을 만들면 “파일을 다시 여는” 대신, 같은 버퍼를 다른 패널에 보여주는 방식입니다.

그리고 **탭(tab)**은 여기서 한 단계 더 나아간 개념이에요. 탭은 윈도의 “상위 컨테이너” 같은 겁니다. 여러 탭을 열면, 같은 Neovim 세션 안에 여러 윈도를 갖게 됩니다. 예를 들어 여러 마이크로서비스를 각각 다른 탭에 열어두고, 한 세션에서 왔다 갔다 하면서 작업할 수 있는 거죠.

이제 이 개념이 정리됐으니, 기본 셋업에 필요한 필수 플러그인들을 봅시다.

### 필요한 플러그인들

가장 먼저 필요한 건 플러그인 매니저입니다. 운영체제에서 패키지 매니저가 동작하는 것과 같은 원리예요.

Packer, Plug, Lazy 등 유명한 옵션이 몇 가지 있는데, 저는 Lazy를 씁니다(제가 Lazy라서요 lol). 이름값을 제대로 해서, 정말 “최대한 게으르게” 플러그인을 설치할 수 있게 해줍니다. 플러그인 git repo만 적어두면 나머지는 알아서 해주거든요. 물론 설정(config)은 직접 작성해야 하지만, 적어도 설치 과정에서의 번거로움은 거의 없습니다.

Lazy는 기본으로 lazy loading도 켜 줘서, 모든 플러그인을 한 번에 로드할 때보다 Neovim이 더 빠르게 뜨는 데도 도움이 됩니다. Lazy를 설치하려면 아래처럼 하면 됩니다.

```lua
-- lazy.nvim 부트스트랩
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not (vim.uv or vim.loop).fs_stat(lazypath) then
    local lazyrepo = "https://github.com/folke/lazy.nvim.git"
    local out = vim.fn.system({ "git", "clone", "--filter=blob:none", "--branch=stable", lazyrepo, lazypath })
    if vim.v.shell_error ~= 0 then
        vim.api.nvim_echo({
            { "Failed to clone lazy.nvim:\n", "ErrorMsg" },
            { out,                            "WarningMsg" },
            { "\nPress any key to exit..." },
        }, true, {})
        vim.fn.getchar()
        os.exit(1)
    end
end
vim.opt.rtp:prepend(lazypath)

-- `mapleader`와 `maplocalleader`는 lazy.nvim을 로드하기 전에 설정해야
-- 매핑이 올바르게 동작합니다.
-- 이 지점은 다른 설정(vim.opt)을 해두기에도 좋은 위치예요.
vim.g.mapleader = " "
vim.g.maplocalleader = "\\"

-- lazy.nvim 설정
require("lazy").setup({
    spec = {
	    -- 여기에 모든 플러그인을 넣습니다
    },
    -- 다른 설정은 여기에서 합니다. 자세한 내용은 문서를 참고하세요.
    -- 플러그인 설치 시 사용할 colorscheme
    install = { missing = true, colorscheme = { "catppuccin-mocha" } },
    -- 플러그인 업데이트 자동 확인
    checker = { enabled = true, notify = false },
}, {
    ui = {
        -- Nerd Font를 사용한다면 icons를 빈 테이블로 두면 됩니다(기본 아이콘 사용).
        -- Nerd Font가 없다면 유니코드 아이콘 테이블을 직접 정의하세요.
        icons = vim.g.have_nerd_font and {} or {
            cmd = '⌘',
            config = '🛠',
            event = '📅',
            ft = '📂',
            init = '⚙',
            keys = '🗝',
            plugin = '🔌',
            runtime = '💻',
            require = '🌙',
            source = '📄',
            start = '🚀',
            task = '📌',
            lazy = '💤 ',
        },
    },
})

```

이건 보일러플레이트(boilerplate)이고, 동일한 내용과 문서는 [여기](https://lazy.folke.io/)에서 받을 수 있습니다.

패키지를 설치하려면 `spec` 객체에 이름을 넣어주면 되고, 나머지는 Lazy가 처리합니다. 예시는 이런 식이에요.

1. 패키지 이름만 쓰는 경우:

```lua
"nvim-lua/plenary.nvim",
```

2. 이름과 `options`를 함께 쓰는 경우:

```lua
{
	'nvim-telescope/telescope.nvim',
	tag = '0.1.8',
	dependencies = { 'nvim-lua/plenary.nvim' }
},
{
	"nvim-treesitter/nvim-treesitter",
	build = ":TSUpdate",
	opts = {
		ensure_installed = { 'bash', 'c', 'diff', 'html', 'lua', 'luadoc', 'markdown', 'vim', 'vimdoc', 'javascript', 'rust', 'typescript' },
		-- 설치되지 않은 언어 자동 설치
		auto_install = true,
		highlight = {
			enable = true,
			-- 일부 언어는 들여쓰기 규칙 때문에 Vim의 정규식 하이라이트 시스템(예: Ruby)에 의존합니다.
			-- 들여쓰기가 이상하게 동작한다면, 해당 언어를
			-- additional_vim_regex_highlighting 목록에 추가하고(또는) indent 비활성화 목록에 넣어보세요.
			additional_vim_regex_highlighting = { 'ruby' },
		},
		indent = { enable = true, disable = { 'ruby' } },
	},
},
```

보시다시피 패키지 설치는 꽤 단순하고, 각 패키지 문서에도(대부분은) 같은 방식이 정리돼 있습니다.

이와 별개로, 개발자라면 대부분 “있으면 좋은” 패키지들도 몇 가지가 있습니다.

1. Undotree
2. Gitsigns
3. LSP
4. Comment
5. 파일 트리(file tree) (선택)
6. 컬러스킴(colorscheme) (선택)

아래에는 별 설명 없이 각 플러그인의 문서 링크와 제가 쓰는 설정만 쭉 적어둘게요. 문서 한 번만 훑어봐도 대부분 이해될 겁니다. 만약 이해가 어려운 부분이 있다면 댓글로 남겨 주세요. 가능한 한 답해보겠습니다.

#### Undotree

문서: [https://github.com/mbbill/undotree](https://github.com/mbbill/undotree)  
설정:

```lua
vim.keymap.set("n", "<leader>u", vim.cmd.UndotreeToggle)
```

#### Gitsigns

문서: [https://github.com/lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)  
설정:

```lua
[vim.keymap.set("n", "<leader>u", vim.cmd.UndotreeToggle)](<local neogit = require('neogit')
neogit.setup {}

require('gitsigns').setup {
	signs = {
		add          = { text = '┃' },
		change       = { text = '┃' },
		delete       = { text = '_' },
		topdelete    = { text = '‾' },
		changedelete = { text = '~' },
		untracked    = { text = '┆' },
	},
	signs_staged = {
		add          = { text = '┃' },
		change       = { text = '┃' },
		delete       = { text = '_' },
		topdelete    = { text = '‾' },
		changedelete = { text = '~' },
		untracked    = { text = '┆' },
	},
	signs_staged_enable = true,
	signcolumn = true,  -- `:Gitsigns toggle_signs`로 토글
	numhl      = false, -- `:Gitsigns toggle_numhl`로 토글
	linehl     = false, -- `:Gitsigns toggle_linehl`로 토글
	word_diff  = false, -- `:Gitsigns toggle_word_diff`로 토글
	watch_gitdir = {
		follow_files = true
	},
	auto_attach = true,
	attach_to_untracked = false,
	current_line_blame = false, -- `:Gitsigns toggle_current_line_blame`로 토글
	current_line_blame_opts = {
		virt_text = true,
		virt_text_pos = 'eol', -- 'eol' | 'overlay' | 'right_align'
		delay = 1000,
		ignore_whitespace = false,
		virt_text_priority = 100,
	},
	current_line_blame_formatter = '%3Cauthor%3E, <author_time:%R> - <summary>',
	sign_priority = 6,
	update_debounce = 100,
	status_formatter = nil, -- 기본값 사용
	max_file_length = 40000, -- 파일이 이 줄 수를 넘으면 비활성화
	preview_config = {
		-- nvim_open_win에 넘기는 옵션들
		border = 'single',
		style = 'minimal',
		relative = 'cursor',
		row = 0,
		col = 1
	},
	on_attach = function(bufnr)
		local gitsigns = require('gitsigns')

		local function map(mode, l, r, opts)
			opts = opts or {}
			opts.buffer = bufnr
			vim.keymap.set(mode, l, r, opts)
		end

		-- 내비게이션
		map('n', ']c', function()
			if vim.wo.diff then
				vim.cmd.normal({']c', bang = true})
			else
				gitsigns.nav_hunk('next')
			end
		end)

		map('n', '[c', function()
			if vim.wo.diff then
				vim.cmd.normal({'[c', bang = true})
			else
				gitsigns.nav_hunk('prev')
			end
		end)

		-- 액션
		map('n', '<leader>hs', gitsigns.stage_hunk)
		map('n', '<leader>hr', gitsigns.reset_hunk)
		map('v', '<leader>hs', function() gitsigns.stage_hunk {vim.fn.line('.'), vim.fn.line('v')} end)
		map('v', '<leader>hr', function() gitsigns.reset_hunk {vim.fn.line('.'), vim.fn.line('v')} end)
		map('n', '<leader>hS', gitsigns.stage_buffer)
		map('n', '<leader>hu', gitsigns.undo_stage_hunk)
		map('n', '<leader>hR', gitsigns.reset_buffer)
		map('n', '<leader>hp', gitsigns.preview_hunk)
		map('n', '<leader>hb', function() gitsigns.blame_line{full=true} end)
		map('n', '<leader>tb', gitsigns.toggle_current_line_blame)
		map('n', '<leader>hd', gitsigns.diffthis)
		map('n', '<leader>hD', function() gitsigns.diffthis('~') end)
		map('n', '<leader>td', gitsigns.toggle_deleted)

		-- 텍스트 오브젝트
		map({'o', 'x'}, 'ih', ':<C-U>Gitsigns select_hunk<CR>')
	end
}>
```

#### LSP

문서: [https://github.com/VonHeikemen/lsp-zero.nvim](https://github.com/VonHeikemen/lsp-zero.nvim)  
설정:

```lua
local lsp_zero = require('lsp-zero')
local cmp_lsp = require("cmp_nvim_lsp")

lsp_zero.on_attach(function(client, bufnr)
    -- 사용 가능한 액션을 보려면 :help lsp-zero-keybindings 참고
    if client.name == "tsserver" then
        client.server_capabilities.document_formatting = false
    end
    lsp_zero.default_keymaps({ buffer = bufnr })
end)

local capabilities = vim.tbl_deep_extend(
    "force",
    {},
    vim.lsp.protocol.make_client_capabilities(),
    cmp_lsp.default_capabilities()
)

-- mason.nvim 사용법을 보려면
-- 여기 참고: https://github.com/VonHeikemen/lsp-zero.nvim/blob/v3.x/doc/md/guide/integrate-with-mason-nvim.md
require('mason').setup({})
require('mason-lspconfig').setup({
    ensure_installed = {
        "lua_ls",
        "tsserver",
        "eslint",
        "rust_analyzer"
    },
    handlers = {
        function(server_name)
            local opts = {}
            if server_name == "tsserver" then
                opts.settings = {
                    implicitProjectConfiguration = {
                        checkJs = true
                    },
                }
            end

            opts.capabilities = capabilities

            require('lspconfig')[server_name].setup(opts)
        end,
    },
})

local cmp = require("cmp")
local luasnip = require('luasnip')
luasnip.config.setup {}
local cmp_mappings = cmp.mapping.preset.insert({
    ["<C-Space>"] = cmp.mapping.complete(),
    ["<C-k>"] = cmp.mapping.select_prev_item(),
    ["<C-j>"] = cmp.mapping.select_next_item(),
    ["<C-b>"] = cmp.mapping(cmp.mapping.scroll_docs(-1), { "i", "c" }),
    ["<C-f>"] = cmp.mapping(cmp.mapping.scroll_docs(1), { "i", "c" }),
    ["<C-y>"] = cmp.config.disable, -- 기본 `<C-y>` 매핑을 제거하고 싶으면 `cmp.config.disable`을 지정하세요.
    ["<C-e>"] = cmp.mapping({
        i = cmp.mapping.abort(),
        c = cmp.mapping.close(),
    }),
    -- 현재 선택된 아이템을 확정합니다. 선택된 게 없으면 첫 아이템을 `select`합니다.
    -- `select`를 `false`로 두면, 명시적으로 선택한 경우에만 확정합니다.
    ["<CR>"] = cmp.mapping.confirm({ select = true }),
    ["<Tab>"] = cmp.mapping(function(fallback)
        if cmp.visible() then
            cmp.select_next_item()
        else
            fallback()
        end
    end, { "i", "s" }),
    ["<S-Tab>"] = cmp.mapping(function(fallback)
        if cmp.visible() then
            cmp.select_prev_item()
        else
            fallback()
        end
    end, { "i", "s" }),
})

cmp.setup({
    snippet = {
        expand = function(args)
            luasnip.lsp_expand(args.body)
        end,
    },
    completion = { completeopt = 'menu,menuone,noinsert' },
    mapping = cmp_mappings,
    sources = {
        { name = 'nvim_lsp' },
        { name = 'luasnip' },
        { name = 'path' },
    },
})

local status, prettier = pcall(require, "prettier")
if not status then
    return
end

prettier.setup({
    bin = "prettierd",
    filetypes = {
        "css",
        "javascript",
        "javascriptreact",
        "typescript",
        "typescriptreact",
        "json",
        "scss",
        "less",
    },
})
```

#### Comment

이건 두 파트로 나뉩니다.

1. Comments(주석 추가)

문서: [https://github.com/numToStr/Comment.nvim](https://github.com/numToStr/Comment.nvim)  
설정:

```lua
local status_ok, comment = pcall(require, "Comment")
if not status_ok then
	return
end

comment.setup({
	pre_hook = function(ctx)
		local U = require("Comment.utils")

		local location = nil
		if ctx.ctype == U.ctype.block then
			location = require("ts_context_commentstring.utils").get_cursor_location()
		elseif ctx.cmotion == U.cmotion.v or ctx.cmotion == U.cmotion.V then
			location = require("ts_context_commentstring.utils").get_visual_start_location()
		end

		return require("ts_context_commentstring.internal").calculate_commentstring({
			key = ctx.ctype == U.ctype.line and "__default" or "__multiline",
			location = location,
		})
	end,
})
```

2. Treesitter Context(현재 언어가 뭔지 Treesitter 컨텍스트 제공)

문서: [https://github.com/nvim-treesitter/nvim-treesitter-context](https://github.com/nvim-treesitter/nvim-treesitter-context)  
설정:

```lua
require 'treesitter-context'.setup {
	enable = true,            -- 플러그인 활성화(나중에 명령으로 켜고/끄기 가능)
	max_lines = 0,            -- 컨텍스트 창이 차지할 최대 줄 수. 0 이하이면 무제한.
	min_window_height = 0,    -- 컨텍스트를 활성화할 최소 창 높이. 0 이하이면 무제한.
	line_numbers = true,
	multiline_threshold = 20, -- 단일 컨텍스트에서 표시할 최대 줄 수
	trim_scope = 'outer',     -- `max_lines` 초과 시 버릴 컨텍스트 라인. 'inner' | 'outer'
	mode = 'cursor',          -- 컨텍스트 계산 기준 라인. 'cursor' | 'topline'
	-- 컨텍스트와 내용 사이 구분자. '-' 같은 단일 문자 문자열이어야 합니다.
	-- 구분자를 설정하면, 커서 라인 위에 최소 2줄이 있을 때만 컨텍스트가 표시됩니다.
	separator = nil,
	zindex = 20,     -- 컨텍스트 창 Z-index
	on_attach = nil, -- (fun(buf: integer): boolean) false를 반환하면 attach 비활성화
}
```

#### 파일 트리(file tree) (선택)

이건 꽤 주관적이고 사람마다 다릅니다. 좋은 파일 트리 플러그인이 많이 있고, 대표적으로 `nvim-tree`, `neotree`, `nerdtree` 등이 있어요.

저는 개인적으로 파일 탐색기를 별로 안 좋아합니다(공간을 많이 먹고, 집중을 깨고, 무엇보다 VS Code가 떠올라서요). 그래서 저는 `yazi.nvim`을 씁니다.

문서: [https://github.com/mikavilpas/yazi.nvim](https://github.com/mikavilpas/yazi.nvim)  
설정:

이건 별도 설정이 필요 없습니다. yazi를 쓴다면 그 설정을 그대로 사용하고, 설치 시 키바인딩만 잡아주면 됩니다.

```lua
{
	"mikavilpas/yazi.nvim",
	event = "VeryLazy",
	keys = {
		-- 👇 이 섹션에서 원하는 키매핑을 고르세요!
		{
			"<leader>pv",
			function()
				require("yazi").yazi()
			end,
			desc = "Open the file manager",
		},
		{
			-- 현재 작업 디렉터리에서 열기
			"<leader>cw",
			function()
				require("yazi").yazi(nil, vim.fn.getcwd())
			end,
			desc = "Open the file manager in nvim's working directory",
		},
	},
	opts = {
		-- netrw 대신 yazi를 열고 싶다면, 자세한 내용은 문서를 참고하세요
		open_for_directories = false,
	},
},
```

#### 컬러스킴(colorscheme) (선택)

이것도 역시 취향이고 사용자마다 다릅니다. 저는 catppuccin을 씁니다.

문서: [https://github.com/catppuccin/nvim](https://github.com/catppuccin/nvim)  
설정:

```lua
{
	"catppuccin/nvim",
	name = "catppuccin",
	priority = 1000
},
```

#### 보너스: 삶의 질(quality of life) 플러그인 몇 가지

제가 개인적으로 더 쓰는 플러그인은 아래와 같습니다.

1. [Harpoon](https://github.com/ThePrimeagen/harpoon)
2. [Neogit](https://github.com/NeogitOrg/neogit)
3. [TODO Domments](https://github.com/folke/todo-comments.nvim)
4. [Mini.nvim](https://github.com/echasnovski/mini.nvim)
5. [Noice.nvim](https://github.com/folke/noice.nvim)
6. [Lualine](https://github.com/nvim-lualine/lualine.nvim)
7. [Autopairs](https://github.com/windwp/nvim-autopairs)
8. [Indent Blankline](https://github.com/lukas-reineke/indent-blankline.nvim)
9. [nvim-ts-context-commentstring](https://github.com/JoosepAlviste/nvim-ts-context-commentstring)
10. [vim-css-color](https://github.com/ap/vim-css-color)
11. [vim-closetag](https://github.com/alvan/vim-closetag)
12. [vim-illuminate](https://github.com/RRethy/vim-illuminate)
13. [goto-preview](https://github.com/rmagatti/goto-preview)
14. [Trouble](https://github.com/folke/trouble.nvim)
15. [Codeium](https://github.com/Exafunction/codeium.vim)

“플러그인이 너무 많은 거 아니에요?”라고 생각할 수도 있는데, 네 맞습니다. 많아요. 그래도 이게 제가 필요로 하는 가장 “기본적인” Neovim 셋업이에요. 더 플러그인을 추가해서 기능을 더 풍부하게 만드는 것도 완전히 괜찮지만, 저는 셋업이 빠르고 안정적이길 원해서, 플러그인이 적을수록 구버전이 되거나 깨지는 걸 덜 걱정해도 되더라고요 xD

## 결론

이렇게 해서 긴 글을 마무리하게 됐네요. 제 이야기를 제외하면(…) 정보가 도움이 됐고 뭔가라도 배워 가셨으면 좋겠습니다. 여기까지 읽으셨다면 시간과 인내에 감사드려요.

글 내용이나 제 글쓰기 스타일, 제가 다룬 디테일, 혹은 제가 놓친 내용 등 뭐든 좋으니 댓글로 남겨주시면 정말 좋겠습니다. 저는 이 커뮤니티로부터 정말 많은 리소스를 얻어서 배우고 성장해 왔고, 이제는 이 커뮤니티에 더 적극적으로 기여하고 싶거든요. 그 방향에 대한 제안도 받고 싶습니다.

이번 주말에 올 다음 글에서 또 뵐게요.

