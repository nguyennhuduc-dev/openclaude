# OpenClaude

<div align="center">
  <img src="docs/assets/openclaude-wordmark.png" alt="OpenClaude — môi trường terminal cho mọi mô hình LLM" width="830">
</div>

**OpenClaude** là công cụ AI hỗ trợ lập trình mã nguồn mở, hoạt động trong terminal và tương thích với các nhà cung cấp mô hình AI trên đám mây hoặc chạy cục bộ.

Bạn có thể sử dụng API tương thích OpenAI, Gemini, GitHub Models, Codex OAuth, Codex, Ollama, Atomic Chat cùng nhiều dịch vụ khác trong một quy trình làm việc thống nhất: nhập yêu cầu, thao tác tệp, sử dụng công cụ, điều phối agent, kết nối MCP, dùng lệnh slash và nhận kết quả theo thời gian thực.

[![PR Checks](https://github.com/Twigpine/openclaude/actions/workflows/pr-checks.yml/badge.svg?branch=main)](https://github.com/Twigpine/openclaude/actions/workflows/pr-checks.yml)
[![Release](https://img.shields.io/github/v/tag/Twigpine/openclaude?label=release&color=0ea5e9)](https://github.com/Twigpine/openclaude/tags)
[![npm downloads](https://img.shields.io/npm/dm/@twigpine/openclaude)](https://www.npmjs.com/package/@twigpine/openclaude)
[![Discussions](https://img.shields.io/badge/discussions-open-7c3aed)](https://github.com/Twigpine/openclaude/discussions)
[![Discord](https://img.shields.io/badge/Discord-tham_gia-5865F2?logo=discord&logoColor=white)](https://discord.gg/k68zFR6AcB)
[![X](https://img.shields.io/badge/X-@twigpine-000000?logo=x&logoColor=white)](https://x.com/twigpine)
[![Security Policy](https://img.shields.io/badge/security-policy-0f766e)](SECURITY.md)
[![License](https://img.shields.io/badge/license-MIT-2563eb)](LICENSE)

Dự án cũng được đồng bộ tại [Twigpine](https://gitlawb.com/node/repos/z6MkqDnb/openclaude).

**Điều hướng:** [Bắt đầu nhanh](#bắt-đầu-nhanh) · [Hướng dẫn cài đặt](#hướng-dẫn-cài-đặt) · [Nhà cung cấp AI](#các-nhà-cung-cấp-được-hỗ-trợ) · [Tính năng](#các-tính-năng-chính) · [Phát triển](#phát-triển-dự-án) · [Tiện ích VS Code](#tiện-ích-vs-code) · [Cộng đồng](#cộng-đồng)

## Đối tác

<table align="center">
  <tr>
    <td align="center"><a href="https://twigpine.com"><img src="https://twigpine.com/logo.png" alt="Twigpine" width="72"></a></td>
    <td align="center"><a href="https://bankr.bot"><img src="https://bankr.bot/favicon.svg" alt="Bankr.bot" width="72"></a></td>
    <td align="center"><a href="https://atomic.chat/"><img src="docs/assets/atomic-chat-logo.png" alt="Atomic Chat" width="72"></a></td>
    <td align="center"><a href="https://mimo.mi.com"><img src="https://mimo.xiaomi.com/mimo-v2-pro/assets/logo.svg" alt="Xiaomi MiMo" width="100"></a></td>
    <td align="center"><a href="https://www.atlascloud.ai/"><img src="docs/assets/atlas-cloud-banner.png" alt="Atlas Cloud" width="120"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://twigpine.com"><strong>Twigpine</strong></a></td>
    <td align="center"><a href="https://bankr.bot"><strong>Bankr.bot</strong></a></td>
    <td align="center"><a href="https://atomic.chat/"><strong>Atomic Chat</strong></a></td>
    <td align="center"><a href="https://mimo.mi.com"><strong>Xiaomi MiMo</strong></a></td>
    <td align="center"><a href="https://www.atlascloud.ai/"><strong>Atlas Cloud</strong></a></td>
  </tr>
</table>

## Vì sao nên dùng OpenClaude?

- Một CLI cho cả API đám mây lẫn mô hình AI chạy cục bộ.
- Thiết lập nhà cung cấp theo hướng dẫn và lưu cấu hình bằng lệnh `/provider`.
- Tích hợp quy trình lập trình với Bash, đọc/ghi/chỉnh sửa tệp, tìm kiếm mã, agent, task, MCP và công cụ web.
- Có tiện ích mở rộng VS Code hỗ trợ khởi chạy và giao diện điều khiển.
- Có nhân vật pixel-art đồng hành, phản hồi khi bạn gửi yêu cầu trong terminal.

## Bắt đầu nhanh

### Yêu cầu hệ thống

- Node.js `>=24.22.1` để cài đặt và chạy bản npm; **Node.js 26 được khuyến nghị**.
- Bun chỉ cần thiết khi biên dịch từ mã nguồn hoặc phát triển dự án.

### Cài đặt

Cài OpenClaude toàn cục bằng npm:

```bash
npm install -g @twigpine/openclaude@latest
```

**Nếu đang nâng cấp từ `@gitlawb/openclaude`:** gói đã chuyển sang phạm vi `@twigpine` và gói cũ không còn được cập nhật. Hãy gỡ gói cũ trước khi cài gói mới:

```bash
npm uninstall -g @gitlawb/openclaude
npm install -g @twigpine/openclaude@latest
```

Thao tác này không xóa cấu hình và phiên làm việc tại `~/.openclaude` và `~/.openclaude.json`. Không nên dùng `--force` để cài đè gói cũ, vì khi gỡ gói cũ sau đó, lệnh `openclaude` có thể bị xóa.

Người dùng Arch Linux cũng có thể cài từ gói AUR do cộng đồng duy trì:

```bash
paru -S openclaude
```

Nếu gặp lỗi `ripgrep not found`, hãy cài ripgrep ở cấp hệ thống và xác nhận lệnh `rg --version` chạy được trong cùng terminal.

Kiểm tra phiên bản và thông tin gói:

```bash
openclaude --version
npm view @twigpine/openclaude dist-tags
npm install -g @twigpine/openclaude@latest
```

### Khởi chạy

```bash
openclaude
```

Một số lệnh hữu ích trong OpenClaude:

- `/provider`: thiết lập nhà cung cấp AI và quản lý cấu hình đã lưu.
- `/onboard-github`: thiết lập GitHub Models.
- `/search`: chọn dịch vụ tìm kiếm web, thêm API key hoặc kiểm tra cấu hình.

> **Lưu ý:** OpenClaude không tự động nạp các tệp `.env` của dự án. Nên dùng `/provider` để thiết lập và lưu hồ sơ nhà cung cấp trong `.openclaude-profile.json`. Nếu muốn dùng biến môi trường trong tệp, chạy `openclaude --provider-env-file .env`. Các biến dùng để gỡ lỗi hoặc điều chỉnh runtime cần được khai báo trong shell hoặc trình khởi chạy.

### Tiếp tục một cuộc trò chuyện

Tiếp tục phiên theo ID hoặc tiếp tục cuộc trò chuyện gần nhất trong thư mục hiện tại:

```bash
openclaude --resume <session-id>
openclaude --continue
```

Thêm `--fork-session` để tạo phiên mới dựa trên lịch sử hội thoại:

```bash
openclaude --resume <session-id> --fork-session
openclaude --continue --fork-session
```

Việc fork chỉ phân nhánh lịch sử hội thoại; không tạo môi trường tệp riêng, không sao chép working tree và không tạo nhánh Git worktree.

### Quản lý cuộc trò chuyện đã lưu

Chạy `/sessions` để xem các cuộc trò chuyện đã lưu của dự án. Chọn một mục để tiếp tục, xóa (có yêu cầu xác nhận) hoặc quay lại danh sách. Có thể nhấn `d` hai lần để xóa một mục; thao tác xóa không thể hoàn tác. Phiên đang sử dụng không xuất hiện trong danh sách này.

### Chạy tác vụ nền

Có thể chạy yêu cầu dài ở chế độ nền:

```bash
openclaude --bg "fix failing tests"
openclaude --bg --name auth-refactor "refactor auth middleware"
openclaude ps
openclaude logs auth-refactor
openclaude logs auth-refactor -f
openclaude kill auth-refactor
```

Các phiên nền là tiến trình con chạy trên máy cục bộ, không phải daemon hay dịch vụ mạng. Nhật ký và thông tin phiên thường nằm trong `~/.openclaude/bg-sessions/`; có thể đổi thư mục cấu hình bằng `OPENCLAUDE_CONFIG_DIR`. Lệnh `openclaude attach <id-or-name>` hiện chỉ hiển thị phiên phù hợp và hướng dẫn dùng `openclaude logs <id> -f`; chức năng gắn lại trực tiếp vào terminal chưa được triển khai cho phiên nền cục bộ.

### Thư mục cấu hình

Theo mặc định, OpenClaude lưu cấu hình tại `~/.openclaude` và `~/.openclaude.json`. Công cụ không đọc `~/.claude`, thư mục `.claude/` của dự án hoặc `CLAUDE_CONFIG_DIR`; bạn không cần cài Claude Code để bắt đầu sử dụng OpenClaude.

Nếu trước đây đã lưu tệp OpenClaude trong đường dẫn `.claude`, hãy chuyển thủ công những thiết lập, lệnh, agent, skill hoặc tác vụ do chính bạn tạo sang vị trí tương ứng trong `.openclaude`. Không sao chép toàn bộ thư mục `.claude` và không sao chép thông tin xác thực của Claude Code.

### Cấu hình OpenAI nhanh

**macOS / Linux:**

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_API_KEY=sk-your-key-here
export OPENAI_MODEL=gpt-4o

openclaude
```

**Windows PowerShell:**

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_API_KEY="sk-your-key-here"
$env:OPENAI_MODEL="gpt-4o"

openclaude
```

Thay `sk-your-key-here` bằng API key hợp lệ của nhà cung cấp bạn sử dụng. Không chia sẻ API key công khai.

### Cấu hình Ollama chạy cục bộ

**macOS / Linux:**

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_BASE_URL=http://localhost:11434/v1
export OPENAI_MODEL=qwen2.5-coder:7b

openclaude
```

**Windows PowerShell:**

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_BASE_URL="http://localhost:11434/v1"
$env:OPENAI_MODEL="qwen2.5-coder:7b"

openclaude
```

Với Ollama, OpenClaude sử dụng API chat gốc của Ollama và mặc định yêu cầu cửa sổ ngữ cảnh 32768 token cho mỗi yêu cầu chat. Có thể điều chỉnh bằng `OPENCLAUDE_OLLAMA_NUM_CTX` hoặc `OLLAMA_CONTEXT_LENGTH`. Xem [hướng dẫn cấu hình nâng cao](docs/advanced-setup.md#ollama-context-length).

## Hướng dẫn cài đặt

- [Hướng dẫn cho người không chuyên kỹ thuật](docs/non-technical-setup.md)
- [Bắt đầu nhanh trên Windows](docs/quick-start-windows.md)
- [Bắt đầu nhanh trên macOS / Linux](docs/quick-start-mac-linux.md)
- [Cấu hình nâng cao](docs/advanced-setup.md)
- [Tự động định tuyến thông minh](docs/smart-routing.md)
- [Định tuyến agent và giới hạn bước](docs/agent-routing.md)
- [Máy chủ gRPC không giao diện](docs/grpc-server.md)
- [Sơ đồ cấu trúc mã nguồn](docs/repo-map.md)
- [Skills](docs/skills.md)
- [Cài đặt trên Android](ANDROID_INSTALL.md)

## Các nhà cung cấp được hỗ trợ

Có thể thiết lập nhà cung cấp qua lệnh `/provider`, biến môi trường hoặc hướng dẫn tương ứng. Danh sách và khả năng hỗ trợ có thể thay đổi theo phiên bản.

| Nhà cung cấp | Cách thiết lập | Ghi chú |
| --- | --- | --- |
| API tương thích OpenAI | `/provider` hoặc biến môi trường | Hỗ trợ OpenAI, OpenRouter, DeepSeek, Groq, Mistral, LM Studio và các máy chủ tương thích endpoint `/v1`. |
| Z.AI GLM Coding Plan | `/provider` hoặc biến môi trường tương thích OpenAI | Dùng `OPENAI_API_KEY` tại `https://api.z.ai/api/coding/paas/v4`; mặc định `glm-5.2`, có lựa chọn hỗ trợ hình ảnh `glm-5.3-flash`. |
| AI/ML API | `/provider` hoặc `AIMLAPI_API_KEY` | [Hướng dẫn](docs/aimlapi-setup.md); dùng `https://api.aimlapi.com/v1` và tự phát hiện các mô hình chat tương thích. |
| Merge Gateway | `/provider` hoặc `MERGE_GATEWAY_API_KEY` | [Hướng dẫn](docs/merge-gateway-setup.md); cổng định tuyến đa nhà cung cấp, hỗ trợ Chat Completions, Responses và chính sách định tuyến. |
| Concentrate | `/provider` hoặc `CONCENTRATE_API_KEY` | Cổng tương thích OpenAI tại `https://api.concentrate.ai/v1`; mặc định `deepseek-v4-flash`. |
| LLMTR | `/provider` hoặc biến môi trường tương thích OpenAI | Cổng đa mô hình tại `https://llmtr.com/v1`; mặc định `deepseek/deepseek-v4-flash` khi dùng cấu hình tương ứng. |
| Command Code | `/provider` hoặc biến môi trường tương thích OpenAI | Cổng tại `https://api.commandcode.ai/provider/v1`; cần API key Command Code. Tích hợp Chat Completions này không hỗ trợ mô hình Claude. |
| ApiSmart | `/provider` hoặc `APISMART_API_KEY` | Dùng `https://gw.apismart.ai/v1`; mặc định `DEEPSEEK_V4_FLASH`. |
| API Route | `/provider` hoặc `API_ROUTE_API_KEY` | Dùng `https://global.api-route.com/v1`; mặc định `claude-sonnet-4-6`. |
| GMI Cloud | `/provider`, `--provider gmi-cloud` hoặc biến môi trường | Dùng `GMI_API_KEY` tại `https://api.gmi-serving.com/v1`; mặc định `Qwen/Qwen3.8-Max`. |
| Hicap | `/provider` hoặc biến môi trường tương thích OpenAI | Tự phát hiện mô hình từ endpoint `/models`; hỗ trợ chế độ Responses cho mô hình `gpt-`. |
| Fireworks AI | `/provider` hoặc biến môi trường | Có danh sách mô hình được tuyển chọn; dùng `FIREWORKS_API_KEY`. |
| LongCat | `/provider` hoặc biến môi trường | API tương thích OpenAI tại `https://api.longcat.chat/openai/v1`; dùng `LONGCAT_API_KEY`. |
| ClinePass | `/provider` hoặc biến môi trường | Cổng mô hình AI có giới hạn sử dụng theo thời gian; dùng `CLINE_API_KEY`. |
| Gemini | `/provider` hoặc biến môi trường | Hỗ trợ API key. |
| Gemini trên Vertex AI | `--provider gemini-vertex` hoặc biến môi trường | Gửi yêu cầu Gemini gốc bằng Google ADC hoặc access token; xem [hướng dẫn](docs/advanced-setup.md#gemini-on-vertex-ai-native). |
| GitHub Models | `/onboard-github` | Có quy trình thiết lập tương tác và lưu thông tin xác thực. |
| Codex OAuth | `/provider` | Đăng nhập ChatGPT trong trình duyệt và lưu thông tin Codex an toàn. |
| Codex | `/provider` | Dùng xác thực từ Codex CLI, bộ lưu trữ an toàn của OpenClaude hoặc biến môi trường. |
| Twigpine Opengateway | Mặc định khi khởi chạy, `/provider` hoặc biến môi trường | Cổng tại `https://opengateway.gitlawb.com/v1`; cần API key từ [Opengateway](https://gitlawb.com/opengateway/keys). |
| OpenCode Zen | `/provider` hoặc biến môi trường | Cổng AI trả phí theo mức sử dụng; dùng `OPENCODE_API_KEY` qua `https://opencode.ai/zen/v1`. |
| OpenCode Go | `/provider` hoặc biến môi trường | Gói thuê bao cho các mô hình mở; dùng `OPENCODE_API_KEY` qua `https://opencode.ai/zen/go/v1`. |
| Xiaomi MiMo | `/provider` hoặc biến môi trường | API tương thích OpenAI tại `https://mimo.mi.com`; dùng `MIMO_API_KEY`. |
| NEAR AI | `/provider` hoặc biến môi trường | Cổng thống nhất hỗ trợ Claude, GPT, Gemini và mô hình mở TEE; dùng `NEARAI_API_KEY`. |
| Cloudflare Workers AI | `/provider` hoặc biến môi trường | Endpoint tương thích OpenAI; dùng `CLOUDFLARE_API_TOKEN` và thay `<ACCOUNT_ID>` bằng ID tài khoản Cloudflare. |
| Ollama | `/provider` hoặc biến môi trường | Chạy suy luận AI cục bộ, không cần API key cho máy chủ cục bộ. |
| Atomic Chat | `/provider`, biến môi trường hoặc `bun run dev:atomic-chat` | Nhà cung cấp mô hình cục bộ; tự phát hiện mô hình đã tải. |
| Bedrock / Vertex / Foundry | Biến môi trường | Các tuyến đám mây thuộc hệ sinh thái Anthropic; Vertex ở đây dành cho Claude trên Vertex AI. |

## Các tính năng chính

- **Quy trình lập trình dựa trên công cụ:** Bash, đọc/ghi/chỉnh sửa tệp, grep, glob, agent, task, MCP và lệnh slash.
- **Phản hồi trực tuyến:** Hiển thị nội dung và tiến trình sử dụng công cụ theo thời gian thực.
- **Gọi công cụ nhiều bước:** Mô hình có thể gọi công cụ, nhận kết quả và tiếp tục xử lý.
- **Hình ảnh:** Hỗ trợ đầu vào hình ảnh bằng URL hoặc base64 ở các nhà cung cấp có khả năng xử lý hình ảnh. Có thể dán ảnh từ clipboard bằng Ctrl+V (Alt+V trên Windows). Giới hạn và yêu cầu kích thước phụ thuộc nhà cung cấp; nếu ảnh không đáp ứng yêu cầu, OpenClaude sẽ thông báo lỗi để người dùng xử lý.
- **Hồ sơ nhà cung cấp:** Thiết lập theo hướng dẫn và lưu cấu hình ở cấp người dùng.
- **Mô hình cục bộ và từ xa:** Dùng API đám mây, máy chủ cục bộ hoặc suy luận trên Apple Silicon.
- **Sơ đồ mã nguồn (repo map):** Tạo bản đồ cấu trúc repository, xếp hạng tầm quan trọng bằng PageRank và có thể tự thêm vào ngữ cảnh khi bật cờ `REPO_MAP`. Dùng `/repomap` để xem; mặc định 2048 token. Xem [docs/repo-map.md](docs/repo-map.md).
- **Nhân vật đồng hành:** Nhân vật pixel-art xuất hiện cạnh lời nhắc và phản hồi khi làm việc.

## Nhân vật đồng hành

Chạy `/buddy` để tạo nhân vật pixel-art. Nhân vật có thể đứng cạnh lời nhắc, chuyển động và thực hiện hiệu ứng khi bạn gửi tin nhắn.

```text
/buddy                  tạo nhân vật lần đầu hoặc tương tác với nhân vật
/buddy set robinhood    cung thủ xanh — bắn tên mỗi lần nhấn Enter
/buddy set kaio         chiến binh tóc vàng — tạo làn sóng năng lượng
/buddy set strawhat      tung cú đấm co giãn
/buddy set merlin       tạo hiệu ứng lấp lánh
/buddy set kage         ném phi tiêu shuriken
/buddy set ember        tạo hiệu ứng lửa rồng
/buddy set corsair      bắn đại bác kèm khói
/buddy name Robin       đổi tên nhân vật
/buddy set random       chọn ngẫu nhiên nhân vật khác
```

Nhân vật tôn trọng cài đặt `prefersReducedMotion`, chuyển sang hình nét đơn trong terminal ít màu và có thể tắt âm/hiệu ứng bằng `/buddy mute`. Cần terminal rộng ít nhất 100 cột để hiển thị sprite đầy đủ.

## Lưu ý về nhà cung cấp mô hình

Các nhà cung cấp không có hành vi hoàn toàn giống nhau:

- Một số tính năng riêng của Anthropic có thể không có ở nhà cung cấp khác.
- Chất lượng sử dụng công cụ phụ thuộc nhiều vào mô hình được chọn.
- Mô hình cục bộ nhỏ có thể gặp khó khăn với chuỗi tác vụ dài, nhiều bước.
- Một số dịch vụ giới hạn số token đầu ra; OpenClaude sẽ điều chỉnh khi có thể.
- Twigpine Opengateway là lựa chọn mặc định khi cài mới và cần API key từ [Opengateway](https://gitlawb.com/opengateway/keys).
- Khả năng của một mô hình cụ thể có thể khác nhau tùy cổng API. Không nên suy ra tính năng của một cổng chỉ dựa vào tên mô hình.
- Xiaomi MiMo hiện chưa hỗ trợ báo cáo `/usage` trong OpenClaude trên tuyến OpenAI-compatible trực tiếp.
- GitHub Copilot mặc định tuần tự hóa việc chạy sub-agent để giảm mức tiêu thụ Premium Request. Xem [Định tuyến agent và giới hạn bước](docs/agent-routing.md#github-copilot-sub-agent-optimization).

Để đạt kết quả tốt, nên chọn mô hình có khả năng gọi công cụ/hàm tốt.

## Agent và định tuyến mô hình

Có thể định tuyến từng agent sang mô hình khác nhau để tối ưu chi phí hoặc phân chia công việc theo thế mạnh của mô hình, giới hạn số bước công cụ của sub-agent bằng `maxSteps`, và điều chỉnh hành vi sub-agent của GitHub Copilot.

Cấu hình có thể nằm trong `agentModels` và `agentRouting` tại `~/.openclaude/settings.json`, phần frontmatter của agent hoặc biến môi trường. Các agent tích hợp gồm `Explore` và `Plan` (phụ thuộc cờ tính năng), `verification` (cần `VERIFICATION_AGENT` và `tengu_hive_evidence`) cùng `code-reviewer` (cần diff inline).

Xem [hướng dẫn định tuyến agent và giới hạn bước](docs/agent-routing.md).

## Tìm kiếm và tải nội dung web

Exa là dịch vụ tìm kiếm web mặc định. Với một số mô hình không phải Anthropic, OpenClaude có thể dùng gói miễn phí không cần API key của Exa; gói này có giới hạn theo giây và theo ngày. Chạy `/search` để chọn dịch vụ, thêm API key hoặc kiểm tra trạng thái:

```text
/search                # chọn dịch vụ tìm kiếm
/search key exa        # thêm API key Exa (ô nhập được ẩn)
/search remove-key     # xóa API key Exa đã lưu
/search status         # xem dịch vụ đang sử dụng
/search test           # thử tìm kiếm
/search anysearch      # chọn AnySearch
/search key anysearch  # tùy chọn thêm API key AnySearch
```

Các dịch vụ khác như Tavily, Brave và Firecrawl có thể được ưu tiên khi đã cấu hình key; DuckDuckGo là phương án dự phòng cuối. Khi dùng Ollama, OpenClaude ưu tiên endpoint Ollama Web Search nếu đã đăng nhập cục bộ. Đặt `OLLAMA_API_KEY` để bật endpoint Ollama lưu trữ làm phương án dự phòng. Đặt `EXA_FREE_TIER=0` nếu không muốn tìm kiếm qua Exa khi chưa có key.

AnySearch có thể được chọn bằng `/search anysearch` hoặc `WEB_SEARCH_PROVIDER=anysearch`. `ANYSEARCH_API_KEY` là tùy chọn; truy cập ẩn danh có giới hạn thấp hơn. `ANYSEARCH_MAX_RESULTS` nhận số nguyên từ 1 đến 10, mặc định là 10. Xem [tài liệu các nhà cung cấp tìm kiếm web](src/tools/WebSearchTool/README_SEARCH_PROVIDERS.md).

> **Lưu ý:** Phương án DuckDuckGo dự phòng có thể bị giới hạn tốc độ, chặn hoặc chịu điều khoản dịch vụ của DuckDuckGo.

Với các backend gốc của Anthropic và Codex Responses, OpenClaude giữ cơ chế tìm kiếm web gốc trừ khi bạn chọn backend cụ thể qua `/search`. Để chọn tìm kiếm Ollama, dùng `WEB_SEARCH_PROVIDER=ollama`.

`WebFetch` hỗ trợ tải nội dung, nhưng phương pháp HTTP cơ bản kết hợp chuyển HTML sang Markdown có thể không hoạt động trên trang cần JavaScript hoặc chặn yêu cầu HTTP thông thường.

Nếu muốn dùng Firecrawl cho tìm kiếm/tải nội dung, hãy khai báo API key:

```bash
export FIRECRAWL_API_KEY=your-key-here
```

Khi Firecrawl được bật, `WebSearch` có thể dùng API tìm kiếm Firecrawl và `WebFetch` có thể dùng endpoint scrape để xử lý trang web được dựng bằng JavaScript. API key là tùy chọn; xem [Firecrawl](https://firecrawl.dev) để biết thông tin gói miễn phí.

## Máy chủ gRPC không giao diện

OpenClaude có thể chạy như một dịch vụ gRPC không giao diện với streaming hai chiều, giúp tích hợp khả năng agent vào ứng dụng khác, pipeline CI/CD hoặc giao diện tùy chỉnh.

```bash
npm run dev:grpc
```

Repository có kèm CLI thử nghiệm. Xem [hướng dẫn máy chủ gRPC](docs/grpc-server.md) để cấu hình và tạo client từ `src/proto/openclaude.proto`.

## Phát triển dự án

Yêu cầu: Node.js `>=24.22.1` (khuyến nghị Node 26) và Bun `1.4.4` để biên dịch từ mã nguồn.

```bash
bun install
bun run build
node dist/cli.mjs
```

Các lệnh phát triển thường dùng:

- `bun run dev`: biên dịch và chạy từ mã nguồn.
- `bun test`: chạy toàn bộ unit test bằng bộ chạy tích hợp của Bun.
- `bun test path/to/file.test.ts`: chạy test cho một tệp cụ thể.
- `bun run test:coverage`: tạo báo cáo coverage tại `coverage/lcov.info` và báo cáo trực quan tại `coverage/index.html`.
- `bun run test:coverage:ui`: dựng lại riêng giao diện báo cáo coverage.
- `bun run smoke`: chạy kiểm tra smoke.
- `bun run doctor:runtime`, `bun run verify:privacy`: kiểm tra runtime và quyền riêng tư.
- `bun run test:provider`, `bun run test:provider-recommendation`: chạy các bộ test liên quan đến nhà cung cấp.

Đo hiệu năng biên dịch cache của launcher:

```bash
bun run build
bun run benchmark:startup
```

Có thể tăng số lần chạy mẫu:

```bash
bun run benchmark:startup -- --warm-runs 40 --cold-runs 10
```

Benchmark và launcher đã biên dịch yêu cầu Node.js `>=24.22.1`; khuyến nghị Node 26. Đặt `NODE_DISABLE_COMPILE_CACHE=1` để tắt compile cache, bao gồm trường hợp chạy V8 coverage cần biên dịch không cache.

Trước khi mở hoặc cập nhật pull request, hãy thực hiện các bước kiểm tra bắt buộc trong [quy trình xác thực trước khi push](CONTRIBUTING.md#validation). Các lệnh kiểm tra hẹp ở trên không thay thế quy trình đó.

## Cấu trúc repository

- `src/`: mã nguồn chính của CLI và runtime.
- `scripts/`: script biên dịch, xác minh và bảo trì.
- `docs/`: hướng dẫn thiết lập, tài liệu phát triển và tài liệu dự án.
- `vscode-extension/openclaude-vscode/`: tiện ích mở rộng VS Code.
- `.github/`: tự động hóa repository, mẫu issue/PR và CI.
- `bin/`: các điểm khởi chạy CLI.

## Tiện ích VS Code

Repository có tiện ích tại [`vscode-extension/openclaude-vscode`](vscode-extension/openclaude-vscode), hỗ trợ khởi chạy OpenClaude, Control Center nhận biết nhà cung cấp, trò chuyện trong trình soạn thảo, giao diện chủ đề và cấu hình tùy chọn **Microsoft Foundry / Azure OpenAI**. Các thông tin như endpoint, API version, deployment và API key được quản lý qua Secret Storage rồi truyền vào terminal được khởi chạy.

Xem [README của tiện ích VS Code](vscode-extension/openclaude-vscode/README.md).

## Bảo mật

Nếu phát hiện lỗ hổng bảo mật, hãy xem [SECURITY.md](SECURITY.md) để biết cách báo cáo.

## Cộng đồng

- [GitHub Discussions](https://github.com/Twigpine/openclaude/discussions): hỏi đáp, chia sẻ ý tưởng và trao đổi cộng đồng.
- [GitHub Issues](https://github.com/Twigpine/openclaude/issues): báo lỗi và đề xuất công việc cụ thể.
- [Discord](https://discord.gg/k68zFR6AcB): tham gia cộng đồng.
- [X / @twigpine](https://x.com/twigpine): cập nhật tin tức và thông báo.

## Đóng góp

Mọi đóng góp đều được hoan nghênh. Với thay đổi lớn, hãy tạo issue trước để thống nhất phạm vi thực hiện. Tham khảo phần [Phát triển dự án](#phát-triển-dự-án) và [quy trình xác thực trước khi push](CONTRIBUTING.md#validation) để biết các bước kiểm tra cần thiết.

## Tuyên bố miễn trừ trách nhiệm

OpenClaude là dự án cộng đồng độc lập, không liên kết, không được Anthropic xác nhận hoặc tài trợ. OpenClaude bắt nguồn từ mã nguồn Claude Code và đã được chỉnh sửa đáng kể để hỗ trợ nhiều nhà cung cấp mô hình và cách sử dụng mở rộng. “Claude” và “Claude Code” là nhãn hiệu của Anthropic PBC.

Xem [LICENSE](LICENSE) để biết chi tiết về giấy phép.

## Giấy phép

Các phần sửa đổi do cộng tác viên OpenClaude thực hiện được cấp phép theo MIT; phần Claude Code được kế thừa vẫn thuộc phạm vi giấy phép của Anthropic. Xem [LICENSE](LICENSE).
