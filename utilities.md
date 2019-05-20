# 📏 Utilities/Services Document

## Danh sách các hàm utils/services

Liệt kê đầy đủ các hàm utils/services tại đây. Có thể sort theo bảng chữ cái (a -> z) để tiện cho việc tìm kiếm.

Loại document này vẫn có thể dùng để mô tả API tuy nhiên không khuyến khích sử dụng. Dev nên cân nhắc lựa chọn các giải pháp API docs khác như [APIDOC.js](http://apidocjs.com/) hoặc [Swagger](https://swagger.io/) để thuận tiện trao đổi giữa front-end và back-end team.

- [getToken](#gettoken)
- [getPageUrlByPath](#getpageurlbypath)

## Chi tiết

Mô tả chi tiết từng hàm utils/services

- Signature (tên hàm + params truyền vào nếu có + kiểu trả về)
- Mô tả về function/method (mục đích)
- Danh sách params nếu có
- Ví dụ bao gồm cú pháp (import, gọi hàm, ...) và kết quả trả về dưới dạng comment

### getToken

```js
getToken(appKey: string?): string
```

> Giải thích (phần này không đưa vào docs)
>
> - Tên hàm: getToken
> - Param(s):
>   - `appKey`: string (optional)
> - Return type: string
>
> Cú pháp này được tham khảo từ cách khai báo biến của [_TypeScript_](https://www.typescriptlang.org/docs/handbook/basic-types.html)

`getToken()` hỗ trợ lấy `accessToken` của ứng dụng hiện tại thông qua `appKey`. Nếu `appKey` không được truyền thì mặc định sẽ lấy `accessToken` đầu tiên trong danh sách token hiện có.

| Param    | Description                      | Type     | Required | Default Value |
| -------- | -------------------------------- | -------- | -------- | ------------- |
| `appKey` | Key của ứng dụng muốn lấy token. | `string` | `fasle`  | --            |

```js
import { getToken } from "./services/common.services";

const eganyToolsAccessToken = getToken("egany-tools");
// => (egany tools' token) eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzaG9wSWQiOiI1Y2E2ZmZiNmYyNDQxNTAwMTcwZWNiZTUiLCJzaG...aadsaGy
const firstAccessToken = getToken();
// => (1st token) eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzaG9wSWQiOiI1Y2E2ZmZiNmYyNDQxNTAwMTcwZWNiZTUiLCJzaG...aadsaGy
```

### getPageUrlByPath

```js
getPageUrlByPath(appKey: string!, to: string!, ...rest: any[]): Promise<string>
```

> Giải thích (phần này không đưa vào docs)
>
> - Tên hàm: getPageUrlByPath
> - Param(s):
>   - `appKey`: string (required)
>   - `to`: string (required)
>   - `rest`: array of `any` (rest ở đây có thể hiểu là các params phụ khác được truyền vào. Đọc thêm [tại đây](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters))
> - Return type: `Promise` với hàm `resolve(string)`
>
> Cú pháp này được tham khảo từ cách khai báo biến của [_TypeScript_](https://www.typescriptlang.org/docs/handbook/basic-types.html)

`getPageUrlByPath()` được dùng trong `SetPositionButton` component để hỗ trợ lấy url trang thiết lập vị trí.

Giá trị trả về có thể là một url (string) hoặc chuỗi rỗng `""` nếu như có lỗi xảy ra. Thông báo lỗi sẽ được in ra ở console.

Các param(s) truyền sau `appKey` và `to` sẽ được tự động bỏ vào param `rest`.

| Param    | Description                                                                         | Type     | Required | Default Value                                       |
| -------- | ----------------------------------------------------------------------------------- | -------- | -------- | --------------------------------------------------- |
| `appKey` | Key của ứng dụng muốn set vị trí.                                                   | `string` | `true`   | --                                                  |
| `to`     | Trang set vị trí. Một số trang được quy định trước nằm tại `/services/constants.js` | `string` | `true`   | --                                                  |
| `rest`   | Handle của collection hoặc product.                                                 | `any[]`  | `false`  | `all` nếu là collection, `undefined` nếu là product |

```js
import { getPageUrlByPath } from "./services/common.services";
import { PAGE_PRODUCT_BY_COLLECTION } from "./services/constants";

// shop-name sẽ tùy thuộc vào thông tin khi login của user
// url sẽ phụ thuộc vào shop của user

const productPageByCollectionUrl = getPageUrlByPath(
  "egany-tools",
  PAGE_PRODUCT_BY_COLLECTION,
  "collection-handle-here"
)
  .then(function(url) {
    // => https://shop-name.haravan.com/products/first-product-in-collection
  })
  .catch(function(error) {});

const customPageUrl = getPageUrlByPath("egany-tools", "/pages/custom-page")
  .then(function(url) {
    // => https://shop-name.myharavan.com/pages/custom-page
  })
  .catch(function(error) {});
```
