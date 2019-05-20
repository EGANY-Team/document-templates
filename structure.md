# 📁 Structure Document

- [Tổng quan](#overview)
- [Chi tiết](#detail)
  - [/docs](#docs)
  - [/functions](#functions)
  - [/public](#public)
  - [/src](#src)
  - [Các file khác](#etc)
- [Tài liệu tham khảo](#ref)

<a name="overview"></a>

## Tổng quan

Mô tả sơ lược về cấu trúc của project, cụ thể:

- Nếu dùng boilerplate thì link tới boilerplate đó. Ví dụ [create-react-app](https://facebook.github.io/create-react-app/docs/getting-started) hoặc [react-boilerplate](https://github.com/react-boilerplate/react-boilerplate).
- Nếu project được tạo bằng tay thì mô tả lại step-by-step quá trình khởi tạo (không cần quá chi tiết).
- Các công nghệ, thư viện, framework, thuật toán sử dụng trong project

<a name="detail"></a>

## Chi tiết

> Mô tả chi tiết cấu trúc project dưới dạng folder và file, đặc biệt nếu như có custom lại từ boilerplate hoặc cấu trúc lạ, không phổ biến.
>
> Bên dưới là một số ví dụ.

<a name="docs"></a>

### **`/docs`**

> Folder tương đối dễ hiểu, chỉ cần mô tả sơ lược. Có thể bỏ qua nếu quá thông dụng.

Chứa tài liệu liên quan tới dự án.

<a name="functions"></a>

### **`/functions`**

> Đây là một thư mục trong có trong boilerplate project khi chạy `firebase init`.
>
> Tuy đã có document từ phía _Firebase_ nhưng vẫn mô tả vì có custom.

Source code cho back-end. Đây là thư mục của [_Firebase Cloud Functions_](https://firebase.google.com/docs/functions).

Hiện tại tất cả code của back-end đều được viết trong file `index.js`. Back-end chạy trên nền tảng [_Node.js_](https://nodejs.org) version 8. (khai báo trong `/functions/package.json`, property `engines`).

Back-end sử dụng một số package chính sau:

- [firebase-admin](https://www.npmjs.com/package/firebase-admin)
- [firebase-functions](https://www.npmjs.com/package/firebase-functions)
- [firebase-tools](https://www.npmjs.com/package/firebase-tools)
- [express.js](https://www.npmjs.com/package/express)
- [cors](https://www.npmjs.com/package/cors)
- [cookie-parser](https://www.npmjs.com/package/cookie-parser)
- [dotenv](https://www.npmjs.com/package/dotenv)

<a name="public"></a>

### **`/public`**

> Mô tả thêm để dev mới có thể dễ dàng tiếp cận. Document của _Firebase_ không mô tả phần này.

Thư mục public của front-end. Đường dẫn relative là `/`.

```html
<!-- đường dẫn tới file /public/image.png -->
<img src="/image.png" alt="image" />
```

<a name="src"></a>

### **`/src`**

> Tương tự như folder `/functions`
>
> Nếu có sử dụng cấu trúc custom thì nên link tới bài hướng dẫn hoặc docs của cấu trúc đó. Cụ thể ở ví dụ bên dưới là bài viết _State Management with React Hooks and Context API in 10 lines of code!_

Source code cho front-end. Được tạo ra từ [`create-react-app`](https://github.com/facebook/create-react-app).

Sơ lược về các thư mục:

- `/components`: chứa stateless component
- `/constants`: khai báo biến constants nằm trong front-end
- `/containers`: chứa stateful component
- `/firebase`: init firebase tại đây
- `/pages`: mỗi trang là một route của front-end
- `/reducers`: [reducer](https://reactjs.org/docs/hooks-reference.html#usereducer) cho các component cần sử dụng
- `/routes`: khai báo routes tại đây
- `/services`: xử lí api request
- `/store`: chứa global state (đọc thêm [tại đây](https://medium.com/simply/state-management-with-react-hooks-and-context-api-at-10-lines-of-code-baf6be8302c))
- `/utils`: các hàm utils hay dùng trong các component

<a name="etc"></a>

### **Các file khác**

> Thường sẽ miêu tả _dotfiles_ (file bắt đầu bằng dấu chấm `.`) hoặc các file config (`.json`, `.yaml`, ...) tại đây.

Một số file cần lưu ý như sau:

- `firebase.json`: Lưu config của firebase project. Khi deploy sẽ dựa vào file này để config môi trường.
- `firestore.indexes.json`, `firestore.rules`: Các file khai báo liên quan tới _Cloud Firestore_. Dùng lệnh `firebase deploy --only firestore` để cập nhật các file này lên firebase project.

<a name="ref"></a>

## Tài liệu tham khảo thêm

> Các tài liệu đọc thêm cho dev để dễ tiếp cận project.

- [React](https://reactjs.org)
- [Firebase Documentation](https://firebase.google.com/docs/web/setup)
- [Cheatsheets collection](https://devhints.io/)
