# Project context

## Mục tiêu
Làm web game 2.5D. Dùng ảnh gen từ ChatGPT làm reference/asset,
chuyển sang Rive (.riv) bằng Rive CLI + RML, có animation và state machine.

## Môi trường
- Rive CLI đã cài (kiểm tra bằng `rive --version`)
- Chỉ dùng tính năng free: preview local, build .riv qua CLI
- Tránh Luau scripting (có thể cần đăng nhập/trả phí khi build)
- Không phụ thuộc Rive Editor

## Pipeline image-to-Rive
1. Ảnh reference: flat vector style, màu khối, bộ phận tách rời, nền trơn
2. Vector hóa ảnh sang SVG (vtracer/potrace hoặc vẽ lại SVG)
3. Chuyển SVG sang RML (tham khảo svg2rml.py trong repo FloridaGames/Rivedemos)
4. Thêm bones, animation, state machine trong RML
5. Review: chụp frame, so với ảnh gốc, sửa lặp đến khi khớp
6. Build .riv, test trong trang HTML dùng @rive-app/canvas

## Cách review
- `rive <project>`: preview tự rebuild khi sửa RML
- Chụp frame headless để so với reference
- 2.5D: tạo input `angle` (-30..30), chụp frame nhiều góc,
  kiểm tra layer che nhau đúng thứ tự

## Tham khảo
- Rive CLI docs: https://rive.app/docs/cli/overview
- img2threejs (triết lý staged pass + review gate): https://github.com/img2threejs/img2threejs
- rive-rs-cli (công cụ cộng đồng, verify/render .riv): https://github.com/George-RD/rive-rs-cli
