# my bricks

<details><summary><h3>在 Windows 10 上搭建工作环境</h3></summary>

1. #### 安装 WSL2 和 Ubuntu 20
在我当前的 Windows 10 版本上，用管理员身份打开 Powershell 程序，并且运行 `wsl --install` 命令，会自动安装 WSL(2) 环境，默认情况下也会同时安装好 Ubuntu 20。

2. #### WSL Ubuntu 安装开发环境
由于 WSL2 目前并不支持 snap，所以建议通过 nvm 来安装 node。如果安装 nvm 遇到 `curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused` 问题，主要是 DNS 受到污染，可以修改本地 DNS 为 `8.8.8.8` 和 `8.8.4.4` 来解决。

3. #### 设置 Windows Terminal 中 WSL Ubuntu 的启动目录
在设置中，找到对应的启动目录栏，将默认的 `%USERPROFILE%` 改为 `\\wsl$\Ubuntu-20.04\home\jsabc`。

3. #### 安装开发工具
在 WSL 环境下，建议使用 Visual Studio Code 编辑器。同时，为了让它和 WSL 能正常配合工作，还需要给它安装 Remote WSL 扩展。在安装完 Remote WSL 扩展之后，可能有必要在 Powershell 中运行 `wsl.exe --shutdown` 命令重启 WSL。

4. #### 配置 Github
详情参考 github 官方文档。
</details>

----

<details><summary><h3>Nuxt.js</h3></summary>

- Nuxt.js
  * assets/
  * components/
  * layouts/
  * middleware/
  * pages/
  * plugins/
  * static/
  * store/
  * nuxt.config.js
</details>

<details><summary><h3>Vue(2).js</h3></summary>

- Vue.js
  * Component
    - name
    - props
    - components
    - mixins[]
    - data()
      - {}
    - computed
      - {}
    - methods
      - {}
    - watch
      - {}
    - beforeCreate()
    - created()
    - beforeMount()
    - mounted()
    - beforeUpdate()
    - updated()
    - beforeDestroy()
    - destroyed()
  * Store(vuex)
    - state()
      - {}
    - getters
      - {}
    - mutations
      - {}
    - actions
      - {}
    - modules
      - {}
</details>

<details><summary><h3>Tailwindcss</h3></summary>

#### 安装 Tailwindcss 及适用于 nuxt 2 的相关依赖

```
yarn add -D tailwindcss postcss@latest autoprefixer@latest @nuxt/postcss8
npx tailwindcss init  // 该命令会自动创建 tailwind.config.js 文件
```

#### 更新 nuxt.config.js 配置

```
export default {
  /**
   * 其他配置
   */
  css: [

    // 新增配置
    '@/assets/css/main.css'
  ],

  buildModules: [

    // 新增配置
    '@nuxt/postcss8'

    /**
    * 如果项目是通过 `yarn create nuxt-app appName` 方式创建的，
    * 并且在创建过程中已选择了集成 tailwindcss；则需要把以下模块移除。
    * 说明：由于 nuxt 2 集成的 tailwindcss 版本较低，不建议使用。
    */
    // '@nuxtjs/tailwindcss'
  ],

  build: {

    /**
    * 新增 postcss 配置
    */
    postcss: {
      plugins: {
        tailwindcss: {},
        autoprefixer: {}
      }
    }
  }
}
```

#### 更新 tailwind.config.js

```
module.exports = {
  content: [

    /**
     * 新增以下配置
     */
    './components/**/*.{js,vue,ts}',
    './layouts/**/*.vue',
    './pages/**/*.vue',
    './plugins/**/*.{js,ts}',
    './nuxt.config.{js,ts}'

  ],
  theme: {
    extend: {}
  },
  plugins: []
}
```

#### 创建 assets/css/main.css 文件

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

参考文档：[Install Tailwind CSS with Nuxt.js](https://tailwindcss.com/docs/guides/nuxtjs)
</details>

<details><summary><h3>Axios</h3></summary>

...

</details>

<details><summary><h3>GraphQL</h3></summary>

...

</details>

----

<details><summary><h3>Mapbox</h3></summary>

...

</details>

<details><summary><h3>Turf</h3></summary>

...

</details>

----

<details><summary><h3>vimrc</h3></summary>

```
" Enable filetype plugins
filetype plugin on
filetype indent on

" Set to auto read when a file is changed from the outside
set autoread
au FocusGained,BufEnter * checktime

" Ignore compiled files
set wildignore=*.o,*~,*.pyc
if has("win16") || has("win32")
    set wildignore+=.git\*,.hg\*,.svn\*
else
    set wildignore+=*/.git/*,*/.hg/*,*/.svn/*,*/.DS_Store
endif

" Always show current position
set ruler

" Always show line numbers
set number

" Configure backspace so it acts as it should act
set backspace=eol,start,indent
set whichwrap+=<,>,h,l

" Ignore case when searching
set ignorecase

" When searching try to be smart about cases
set smartcase

" Highlight search results
set hlsearch

" Makes search act like search in modern browsers
set incsearch

" Don't redraw while executing macros (good performance config)
set lazyredraw

" For regular expressions turn magic on
set magic

" Enable syntax highlighting
syntax enable
" set termguicolors
colorscheme default

" Set utf8 as standard encoding and en_US as the standard language
set encoding=utf8

" Use Unix as the standard file type
set ffs=unix,dos,mac

" Turn backup off, since most stuff is in SVN, git etc. anyway...
set nobackup
set nowb
set noswapfile

" Use spaces instead of tabs
set expandtab

" Be smart when using tabs ;)
set smarttab

" 1 tab == 4 spaces
set shiftwidth=2
set tabstop=2

" Linebreak on 500 characters
set lbr
set tw=500

set ai "Auto indent
set si "Smart indent
set wrap "Wrap lines

hi Visual term=reverse cterm=reverse guibg=Grey

hi CursorLine cterm=bold ctermbg=none ctermfg=none
hi CursorLineNr cterm=bold ctermbg=none ctermfg=none

hi TabLine cterm=none ctermbg=none ctermfg=none
hi TabLineFill cterm=none ctermbg=none ctermfg=none
hi TabLineSel cterm=reverse ctermbg=none ctermfg=red

hi Folded cterm=none ctermbg=none ctermfg=none
hi FoldColumn cterm=none ctermbg=none ctermfg=none

" Go to tab by number
noremap <leader>1 1gt
noremap <leader>2 2gt
noremap <leader>3 3gt
noremap <leader>4 4gt
noremap <leader>5 5gt
noremap <leader>6 6gt
noremap <leader>7 7gt
noremap <leader>8 8gt
noremap <leader>9 9gt
noremap <leader>0 :tablast<cr>

noremap <C-e> :Explore
noremap <C-t> :tabedit
```
</details>
