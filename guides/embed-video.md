# 🔗 Hướng dẫn chèn video vào Markdown

## Giới thiệu

Vì [_Github_](https://github.com) không hỗ trợ video trong file [_Markdown_](https://daringfireball.net/projects/markdown/syntax) nên chúng ta sẽ làm theo hướng dẫn này để chèn video vào document.

## Chi tiết

### Cấu trúc

Thay vì chèn trực tiếp video vào document, chúng ta sẽ tạo ra "fake video".

Fake video bao gồm 2 thành phần:

- Preview image
- Video URL

### Các bước thực hiện

**1. Tạo Preview Image **

Nếu như video nằm tại [_Youtube_](https://www.youtube.com) thì ta có thể lấy hình thumbnail với link như sau: `https://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg`.

Với YOUTUBE_VIDEO_ID lấy như hình:
![youtube video id guide](../images/youtube-video-guide.png)

Đối với video ở những nguồn khác, dev có thể tự chụp preview image hoặc sử dụng link preview image khác nếu có.

Cách link hình preview vào markdown:

```md
Cú pháp:

![Video title here](preview_img_url)

Ví dụ:

![LẠC TRÔI | OFFICIAL MUSIC VIDEO | SƠN TÙNG M-TP](https://img.youtube.com/vi/Llw9Q6akRo4/0.jpg)

![Custom preview image](./images/custom-preview.png)
```

Kết quả:

![LẠC TRÔI | OFFICIAL MUSIC VIDEO | SƠN TÙNG M-TP](https://img.youtube.com/vi/Llw9Q6akRo4/0.jpg)

**2. Gắn link cho hình preview **

Sau khi có hình preview, hay cụ thể ở đây là đoạn code `![Video title here](preview_img_url)`. Chúng ta sẽ bọc Preview Image bằng video url. Từ đó có "fake video"

```md
Cú pháp:

[![Video title here](preview_img_url)](video_url)

Ví dụ:

[![LẠC TRÔI | OFFICIAL MUSIC VIDEO | SƠN TÙNG M-TP](https://img.youtube.com/vi/Llw9Q6akRo4/0.jpg)](https://www.youtube.com/watch?v=Llw9Q6akRo4)
```

Kết quả:

[![LẠC TRÔI | OFFICIAL MUSIC VIDEO | SƠN TÙNG M-TP](https://img.youtube.com/vi/Llw9Q6akRo4/0.jpg)](https://www.youtube.com/watch?v=Llw9Q6akRo4)

## Tham khảo thêm

Bài hướng dẫn được tham khảo từ https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#youtube-videos
