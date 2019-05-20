# 🌀 Hướng dẫn tạo Table of Contents (Index) trong Markdown

## Giới thiệu

Ở một số document với nội dung lớn (dài), người đọc sẽ có nhu cầu chọn lọc section để đọc thay vì đọc từ trên xuống.

Hướng dẫn này sẽ giúp các bạn tạo ra một mục lục cho document của mình.

## Chi tiết

### Cấu trúc

Mục lục chỉ đơn giản là một list (hoặc ordered list) được link tới các section tương ứng. Bạn cũng có thể link tới một document khác tại mục lục, miễn là nó có liên quan tới document hiện tại.

**Lưu ý:** Nếu bạn link tới một file `.md` khác nằm trong cùng project, bạn phải sử dụng đường dẫn relative. Đọc thêm [tại đây](https://www.coffeecup.com/help/articles/absolute-vs-relative-pathslinks/)

```md
- [Main menu 1](#main-menu-1)
  - [Sub menu 1.1](#sub-menu-1)
  - [Sub menu 1.2](#sub-menu-2)
- [Main menu 2](#main-menu-2)
- [External menu 3](https://egany.com)
```

Demo:

- [Main menu 1](#main-menu-1)
  - [Sub menu 1.1](#sub-menu-1)
  - [Sub menu 1.2](#sub-menu-2)
- [Main menu 2](#main-menu-2)
- [External menu 3](https://egany.com)

### Các bước thực hiện

**1. Tạo menu**

Tùy thuộc vào cách tổ chức của từng document mà mục lục sẽ khác nhau. Phần này sẽ do developer quyết định.

```md
- Giới thiệu
- Cài đặt
  - Development
  - Production
- Tham khảo thêm
```

**2. Gắn link**

Mặc định link của **heading** sẽ theo quy tắc sau:

- Chuyển tất cả kí tự thành lowercase (viết thường)
- Thay khoảng trắng (space) thành dấu gạch ngang (`-`)

**Lưu ý:** Markdown sẽ không tự trim khoảng trắng giữa các từ với nhau nên tất cả các khoảng trắng **giữa các từ** sẽ chuyển thành dấu gạch ngang (`-`). Khoảng trắng đầu và đuôi sẽ được trim như bình thường.

Ví dụ:

```md
## Introduction

Sẽ có link là #introduction

## Getting started

Sẽ có link là #getting-started

## Many Spaces In Between (6 khoảng trắng giữa Spaces và In)

Sẽ có link là #many-spaces------in-between (6 dấu gạch ngang)
```

Quy tắc trên áp dụng cho tất cả ngôn ngữ. Tuy nhiên, do Github không hỗ trợ encode url nên nếu sử dụng `#giới-thiệu` thì đường link sẽ bị mất.

Cách khắc phục như sau:

**2.1 Tạo link ảo ngay trên heading**

Lưu ý cách đặt tên để tránh trường hợp bị trùng. Khuyến khích sử dụng quy tắc đặt tên [_BEM_](http://getbem.com/)

```md
<a name="intro"></a>

## Giới thiệu
```

**2.2 Refer tới heading bằng link ảo**

Link ảo sẽ là `#` kèm theo tên của tag <a></a>. Theo ví dụ trên thì link là `#intro`

```md
- [Giới thiệu](#intro)
```
