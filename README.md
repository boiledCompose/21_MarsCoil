## Coil

Coil은 이미지를 다운로드하고 버퍼링 및 디코딩을 하고 캐시하는 것을 도와주는 외부 라이브러리다.

<br>

### Coil 종속 항목 추가

- `build.gradle.kts (Module:app)`의 `dependencies` 섹션에 다음 코드 즐을 추가한다.

```gradle
// Coil
implementation("io.coil-kt:coil-compose:2.4.0")
```

### AsyncImage 컴포저블

`AsyncImage`는 이미지 요청을 비동기식으로 실행하고 결과를 렌더링하는 컴포저블이다.


```kotlin
// Example code
AsyncImage(
    model = ImageRequest.Builder(LocalContext.current)
        .data("https://example.com/image.jpg")
        .crossfade(true)
        .build(),
    placeholder = painterResource(R.drawable.placeholder),
    contentDescription = stringResource(R.string.description),
    contentScale = ContentScale.Crop,
    modifier = Modifier.clip(CircleShape)
)
```
- `model` 인수는 다운로드할 이미지를 나타내며, `ImageRequest.data` 또는 `ImageRequest` 자체일 수 있다.
   
   - `data`는 이미지의 URL을 인수로 받는다.
   - `crossfade`는 크로스페이드 애니메이션 적용 여부를 나타낸다.

- `placeholder`는 이미지가 없을 때 나타낼 이미지 리소스를 나타낸다.
- `contentScale`은 이미지 크기를 조정하는데 쓰인다.

## Image 속성

### ContentScale

   - `Fit`: 기본값, 가로세로 비율을 유지하면서 경계에 맞게 확대/축소 조정
   - `Crop`: 화면의 사용 가능한 공간에 맞게 이미지를 가운데 중심으로 자름
   - `FillHeight`: 경계가 이미지의 세로와 일치하도록 이미지 크기를 조정
   - `FillWidth`: 경계가 이미지의 가로와 일치하도록 이미지 크기를 조정
   - `FillBound`: 기본 비율을 무시하고 경계에 맞게 이미지를 확대/축소 조정
   - `inside`: 경계 내에서 가로세로 비율을 유지하도록 크기를 조정. 만약 이미지가 원래 작다면 조정하지 않음
   - `None`: 원본 이미지 크기대로 삽입

