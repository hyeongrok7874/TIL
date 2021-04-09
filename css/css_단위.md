# css 단위

## px

> px는 절대적인 값입니다.

## rem

> rem 은 상대적인 값입니다. 하지만 오직 <html> 태그의 font-size에만 영향을 받습니다.<br>
>2rem은 <html> 태그의 font-size의 2배 크기입니다.

## em

> em도 rem과 마찬가지로 상대적인 값입니다. em은 자기 자신의 font-size를 기준으로 합니다.

## 퍼센트(%)

> % 역시 상대적인 값이겠죠? %는 어느 항목에서 쓰이냐에 따라 다른 기준이 적용됩니다.<br>
> 예를 들어 font-size에서 %가 쓰일 경우, 상위 요소의 font-size에 곱해주는 방식으로 계산합니다.<br>
> %가 margin이나 padding의 단위로 사용될 경우, 상위 요소의 width를 기준으로 계산됩니다.<br>
> margin-top이나 padding-bottom 등 세로(상하) 속성를 조절할 때에도 상위 요소의 height가 아닌 width를 기준으로 계산된다는 것입니다.