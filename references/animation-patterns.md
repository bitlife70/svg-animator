# SVG Animation Patterns

## 1. Consistent Packet Flow (Professional Standard)
모든 경로(Path)를 가로지르는 일관된 글로우 패킷 애니메이션입니다.
```xml
<defs>
  <filter id="packet-glow" x="-50%" y="-50%" width="200%" height="200%">
    <feGaussianBlur stdDeviation="2.5" result="blur" />
    <feComposite in="SourceGraphic" in2="blur" operator="over" />
  </filter>
</defs>

<!-- 경로 정의 -->
<path id="flow-path" d="..." stroke="#94a3b8" stroke-width="2" fill="none" />

<!-- 패킷 흐름 (애니메이션) -->
<g filter="url(#packet-glow)">
  <circle r="4" fill="#38bdf8">
    <animateMotion dur="2s" repeatCount="indefinite" path="..." />
  </circle>
</g>
```

## 2. Orthogonal Bypass (직각 우회 라우팅)
박스 내용을 가리지 않기 위해 직각으로 꺾여 나가는 경로 설계입니다.
- **Good**: `M 100,100 L 150,100 L 150,200 L 300,200`
- **Bad**: 박스를 바로 대각선으로 가로지르는 설계

## 3. Pulse Effect (Scaling & Opacity)
노드가 살아있는 것처럼 박동하는 효과입니다.
```xml
<circle cx="100" cy="100" r="10" fill="#38bdf8">
  <animate attributeName="r" values="10;13;10" dur="2s" repeatCount="indefinite" />
  <animate attributeName="opacity" values="1;0.5;1" dur="2s" repeatCount="indefinite" />
</circle>
```

## 4. Sophisticated Easing
부드러운 움직임을 위해 `keyTimes`와 `keySplines`를 활용하세요.
- Ease-in-out: `0.42, 0, 0.58, 1`
