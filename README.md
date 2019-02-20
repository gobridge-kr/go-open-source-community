# Go, Open Source, Community

8 July 2015

### Welcome

[이건 제 Gophercon 2015 오프닝 키노트의 문서본입니다. [키노트 비디오는 여기서 볼 수 있습니다.](https://www.youtube.com/watch?v=XvZOdpd_9tc)]

이 자리에 참석하기 위해 덴버까지 와주셔서 감사합니다, 그리고 비디오로 이 영상을 보고 계신 분들께도 감사의 말씀을 드립니다. 여러분의 첫번째 Gophercon 이라면, 환영합니다. 작년에도 오셨었다면, 잘 돌아오셨습니다. 운영자 분들께도 이런 행사가 열릴 수 있게 해주신 모든 일에 감사드립니다. 여기 있게 되고 여러분 모두에게 발표를 할 수 있게 되어 신나네요.

저는 구글의 Go 프로젝트와 Go 팀의 기술 리더입니다. 이 역할을 Rob Pike 와 함께 하고 있구요. 이 역할에서, 저는 Go 오픈소스 프로젝트에 대한 전반적인 것들, 특히 이게 어떻게 굴러가는지, 오픈소스가 되는게 무슨 의미를 갖는지, 그리고 구글 내외의 기여자들과의 상호작용에 대해 생각하는데에 많은 시간을 보냅니다. 오늘 저는 제가 Go 프로젝트를 어떻게 생각하는지 공유하고, 거기에 기반해서 제가 Go 오픈소스 프로젝트의 발전을 어떻게 바라보는지 설명하겠습니다.

### Why Go?

시작하기에 앞서, 프로젝트의 시작으로 돌아가 보겠습니다. 우리는 왜 Go 프로젝트를 시작했을까요?

Go 는 프로그래머들을 더 생산적으로 만들려는 시도입니다. 우리는 구글의 소프트웨어 개발 프로세스를 개선하고 싶었습니다만, 구글이 가지고 있던 문제는 구글만의 것이 아니었습니다.

두개의 가장 중요한 목표가 있었습니다.

첫번째 목표는 확장 가능한 동시성 문제를 해결할 수 있는 더 나은 언어를 만드는 것이었습니다. 확장 가능한 동시성이란 말로 제가 의미하는건 천개의 백엔드 서버를 네트워크 트래픽을 앞뒤로 보냄으로써 조정하는 것과 같이 많은 문제를 동시적으로 처리하는 소프트웨어입니다.

오늘날, 그런 종류의 소프트웨어는 더 짧은 이름을 가지고 있죠: 우린 그걸 클라우드 소프트웨어라고 부릅니다. Go 는 클라우드가 소프트웨어를 돌리기 전부터 클라우드를 위해 설계되었다고 해도 무방합니다.

더 큰 목표는 확장 가능한, 동작하고 있고 많은 사람들에 의해 사용되고 있는, 협동이 제한되어 있는, 그리고 수년간 유지되어오고 있는 소프트웨어의 개발에서의 도전 과제를 해결할 수 있는 더 나은 환경을 만드는 것이었습니다. 구글에는 수천명의 엔지니어가 있는데, 이들은 코드를 작성하고 서로 공유하고 일이 완료되도록 노력하고 남들의 작업물을 가능한 재사용하고 십여년이 넘게 오래된 역사를 갖는 코드베이스 위에서 작업하고 있습니다. 엔지니어들은 종종 남들에 의해 작성되었거나 그들이 몇년 전에 작성해서 남이 작성한 것이나 마찬가지인 코드 위에서 작업하거나 최소한 그 코드를 들여다 봅니다. 

구글 안의 이 상황은 GitHub 같은 곳에서 확인된 것처럼 커다란 현대 오픈소스 개발 과정에 흔합니다. 이 때문에, Go 는 오픈소스 프로젝트에 잘 맞고, 오랜 기간 커다란 커뮤니티로부터의 기여를 관리하고 받아들일 수 있었습니다.

저는 Go 의 성공이 Go 가 클라우드 소프트웨어에 잘 맞고, Go 가 오픈소스 프로젝트에 잘 맞으며, 우연히도, 이 두가지가 소프트웨어 업계에서 중요성과 대중성 측면에서 성장하고 있다는 사실로 설명된다고 믿습니다.

다른 사람들도 비슷한 관찰을 했습니다. 여기 두개의 관찰이 있습니다. 작년, RedMonk.com 에서, Donnie Berkholz 는 “[Go as the emerging language of cloud infrastructure](http://redmonk.com/dberkholz/2014/03/18/go-the-emerging-language-of-cloud-infrastructure/)” 라는 글을 썼는데, 여기서 “[Go] 프로젝트는 ... 클라우드 위주이거나 분산 시스템이나 영구적이지 않은 환경들을 처리하기 위해 만들어졌습니다.” 라고 했습니다.

올해, Texlution.com 에서, 이 사람은 “[Why Golang is doomed to succeed](https://texlution.com/post/why-go-is-doomed-to-succeed/)” 라는 글을 썼는데, 여기서는 이 거대 규모 개발에 대한 집중은 어쩌면 구글 스스로보다 오픈소스에 더 잘 맞을수도 있다고 했습니다: “이 오픈소스에의 적합성은 여러분이 더 많은 Go 프로그램을 주변에서 보게 될 것이라고 생각하는 이유입니다 ... ”

### The Go Balance

Go 는 어떻게 그것들을 이룰까요?

어떻게 확장성 있는 동시성과 확장성 있는 소프트웨어 개발을 쉽게 만들었을까요?

대부분의 사람들이 이 질문에 대해 채널과 고루틴, 인터페이스, 빠른 빌드, go 명령, 그리고 좋은 도구 지원에 대해 이야기하는 것으로 답합니다. 그것들은 모두 이
질문에 대한 대답의 중요한 부분들입니다만, 저는 그 뒤에 더 넓은 아이디어가 있다고 생각합니다.

전 그 아이디어를 Go 의 균형이라고 생각합니다. 모든 소프트웨어 설계에는 상충되는 문제가 있고, 여러분이 앞으로 보게될 모든 문제를 해결하려는 자연스런 경향이 있게 마련입니다. 그러는 대신, 우리는 여러분이 자신의 문제에 대한 각자의 해결책을 쉽게 만들기 충분하게만 하려고 했습니다.

제가 Go 의 선택된 균형을 요약하자면 이렇습니다: __덜 하라. 더 가능하게 하라.__

덜 하되, 더 가능하게 하라.

Go 는 모든걸 할 수는 없습니다. 우린 그래선 안됩니다. 하지만 우리가 그걸 하려 한다면, Go 는 몇가지 일들을 잘 할 겁니다. 우리가 그것들을 주의깊게 선택한다면, 우리는 개발자들이 그들에게 필요한, 그리고 이상적으로는 다른 사람들이 만든 해결책과 도구들과 함께 사용될 수 있는, 해결책과 도구들을 쉽게 만들 수 있는 토대를 줄 수 있습니다.

### Examples

이걸 몇가지 예와 함께 설명해 보죠.

먼저, Go 언어의 자체의 크기입니다. 우리는 가능한 한 적은 컨셉만을 언어에 넣으려 노력했는데, 이는 커다란 개발자 커뮤니티의 다른 부분들에서 만들어지는 상호간에 이해되지 않는 은어들을 방지하기 위해서였습니다. 어떤 아이디어도 그게 핵심만을 포함하도록 단순화 되고 그게 추가됨으로써 생기는 복잡도를 정당화 할만큼 분명한 이익이 있다는 게 확실시 되기 전까지는 Go 에 들어오지 않았습니다.

일반적으로, 우리가 Go 가 잘 하길 바라는 100가지 일이 있다면, 우린 100개의 분리된 변경사항을 만들 수 없습니다. 그대신, 우리는 그 설계 공간을 연구, 이해하려 노력하고 나서 상호간에 잘 동작하고 100가지 중 90가지는 가능하게 하는 몇가지 변경사항을 정의합니다. 우리는 언어를 부풀리는 걸 막기 위해, 그리고 오늘에는 중요해 보이지만 내일에는 그렇지 않을 수도 있는 특수한 사용처를 위해 복잡성을 더하는 걸 막기 위해, 남아 있는 10가지는 포기하고자 합니다.

언어를 작게 유지하는건 더 중요한 목표를 가지고 있습니다. 작게 되는 것은 Go 를 배우기 쉽게, 이해하기 쉽게, 구현하기 쉽게, 재구현하기 쉽게, 디버깅하기 쉽게, 수정하기 쉽게, 그리고 발전하기 쉽게 해줍니다. 덜 하는게 더 많은 걸 가능하게 합니다.

이는 우리가 다른 사람들의 많은 아이디어에 대해 안된다고 말한다는 걸 의미함을 짚고 넘어가야겠습니다만, 우린 우리 스스로의 아이디어들에 대해서는 안된다는 말을 더 많이 했음을 분명히 말씀드립니다.

다음으로, 채널과 고루틴입니다. 동시적이고 병렬적인 연산을 어떻게 구조하고 조직해야 할까요? 뮤텍스와 condition variable 은 매우 일반적입니다만 너무 저수준이어서 올바르게 사용하기가 어렵습니다. OpenMP 와 같은 병렬 수행 프레임웍은 너무 고수준이어서 문제의 좁은 영역만을 해결할 수 있습니다. 채널과 고루틴은 이 두 극단의 가운데에 있습니다. 이것들 자체로는 많은 문제의 해결책이 되지 않습니다. 하지만 이것들은 동시성 소프트웨어의 흔한 문제들을 위한 해결책을 만드는데 쉽게 사용될 수 있기 충분할 만큼 강력합니다.

다음으로, 타입과 인터페이스입니다. 정적 타입을 갖는 것은 유용한 컴파일 타임 체크를 가능하게 하는데, 이는 파이썬이나 루비와 같은 동적 타입 언어들에서는 존재하지 않는 것입니다. 동시에, Go 의 정적 타입 기능은 전통적인 정적 타입 언어들의 중복들을 방지해서, 더 가볍게 느껴지고, 동적 타입 언어처럼 느껴지게 합니다. 이게 사람들이 처음 알아차린 것들 중 하나였고, Go 를 초기에 적용한 사람들 중 많은 사람들이 동적 타입 언어쪽에서 나왔습니다.

Go 의 인터페이스는 Go 의 핵심 부분입니다. 특히, Java 나 정적 계층 구조의 다른 언어에서의 ``implements'' 선언을 제거하는 것은 인터페이스를 가볍고 융녀하게 만듭니다. 그 경직된 계층을 갖지 않는 것은 존재하는, 관계 없는 제품 구현을 설명하는 테스트 인터페이스 같은 관용구를 가능하게 합니다. 덜 하는게 더 많은 걸 가능하게 합니다.

다음으로, 테스트와 벤치마크입니다. 대부분의 언어에 테스트나 벤치마크 프레임웍이 부족이 있나요? 테스트와 벤치마크 사이에 합의가 있나요?

Go 의 테스트 패키지는 이 주제의 모든 일면을 다루려 만들어지지 않았습니다. 그대신, 대부분의 고수준 도구 사용에 필요한 기본 컨셉을 제공하기 위해 만들어졌습니다. 패키지는 통과하거나, 실패하거나, 생략되는 테스트 케이스들을 갖습니다. 패키지는 수행되고 다양한 수치로 측정될 수 있는 벤치마크들을 갖습니다.

여기서 덜 하는 것은 이 컨셉들을 그 핵심 부분으로 줄임으로써, 더 기능이 많은 도구들이 상호작용할 수 있게끔 공유된 어휘를 만들려는 시도입니다. 이 합의는 Miki Tebeka 의 go2xunit 변환기, 또는 benchcmp 와 benchstat 벤치마크 분석 도구들과 같은 고수준 테스트 소프트웨어가 만들어질 수 있게 합니다.

기본 컨셉의 표현에 대한 합의가 있기 때문에, 이런 고수준 도구는 사용되기 위한 특수한 노력 없이도 모든 Go 패키지를 위해 동작하며, 서로간에도 상호간 동작하는데, 예를 들어, go2xunit 은 benchstat 의 사용을 방해하지 않는데, 만약 이 도구들이 예를 들어 경쟁 테스팅 프레임웍의 플러그인이라면 서로의 사용을 방해했을 겁니다. 덜 하는게 더 많은 걸 가능하게 합니다.

다음으로, 리팩토링과 프로그램 분석입니다. Go 는 커다란 코드 베이스를 위한 것이기 때문에, 우린 소스코드의 자동화된 관리와 업데이트의 지원을 필요로 할 것을 알고 있었습니다. 우리는 또한 이 주제가 곧바로 구현되기엔 너무 크다는 것도 알았죠. 하지만 우린 우리가 해야만 하는 한가지를 알고 있었습니다. 다른 설정에 맞춰 자동적으로 프로그램을 변경하려 시도한 우리의 경험 상으로, 우리가 마주한 가장 큰 장벽은 수정된 프로그램을 개발자들이 받아들일 수 있는 포맷으로 만드는 것이었습니다.

다른 언어들에서는 다른 팀들이 다른 포맷 규약을 사용하는게 흔합니다. 프로그램에 의한 수정이 잘못된 규약을 사용하면, 소스 파일의 일부분을 다른 부분들과 다르게 보이게 만들거나, 전체 파일을 새로운 포맷으로 만들어서 불필요하고 원하지 않았던 변화를 초래할 겁니다.

Go 는 이 문제가 없습니다. 우린 이 언어가 gofmt 를 사용할 수 있게 설계했고, 우린 gofmt 의 포맷이 모든 Go 프로그램에 적합하게끔 열심히 작업했으며, 우린 gofmt 가 최초의 공개된 배포 첫날부터 사용될 수 있도록 했습니다. 여러분은 특정한 변화가 사람에 의해 만들어졌는지 컴퓨터에 의해 만들어졌는지 말할 수 없습니다. 우린 명시적 리팩토링 지원을 제공하지 않습니다. 모두에게 합의된 포맷 알고리즘을 만드는 것은 개별적인 도구들이 개발되고 상호 동작하게 만드는 공유된 기반이 되기에 충분했습니다. Gofmt 는 예컨대 gofix, goimports 같은 다른 도구들이 만들어지는걸 가능하게 했습니다. 전 이게 이제 시작이라고 봅니다. 훨씬 많은 것들이 만들어질 수 있습니다.

마지막으로, 소프트웨어의 빌드와 공유입니다. Go 버전 1을 향한 개발에서, 우리는 goinstall 을 만들었고 이건 우리 모두 "go get" 이라고 알고 있는 그것이 되었습니다. 이 도구는 github.com 같은 사이트로의 import 경로를 처리하는, 나중에는 HTTP 요청을 만듦으로써 다른 사이트로의 경로를 처리하는, 부가 설정이 필요없는 표준적 방법을 정의했습니다. 이 모두가 합의한 처리 알고리즘은 그런 경로들에 대해 동작하는 다른 도구들이 만들어질 수 있게 했는데, 대표적으로 Gary Burd 의 godoc.org 가 있겠습니다. 이걸 사용해 본 적이 없다면, godoc.org/the-import-path 에 가보세요, 이 웹 사이트는 유효한 모든 "go get" import 경로를 보여주고, 그 코드를 가져오고 그걸 위한 문서를 여러분에게 보여줄 겁니다. 이것의 좋은 부가적 효과 가운데 하나는 godoc.org 가 공개적으로 사용 가능한 Go 패키지들의 개략적인 마스터 리스트로 동작하게 한 것입니다. 우린 import 경로에 분명한 의미를 줬을 뿐입니다. 덜 하고, 더 많은 걸 가능하게 하세요.

이런 도구 사용 예제들 중 많은 것이 공유된 협약을 이루는 것에 관한 것이란 걸 알아차렸을 겁니다. 가끔 사람들은 이걸 두고 Go 가 "독단적"이라고 합니다만, 그보다 깊은 함의가 있습니다. 공유된 협약의 한계에 합의하는 것은 상호작용하는 더 넓은 종류의 도구들을 만들 수 있게 하는 방법인데, 그 모든 것들이 같은 기반 언어를 사용하기 때문입니다. 이건 덜 하고 더 많은 걸 가능하게 하는 매우 효과적인 방법입니다. 특히, 많은 경우에 우리는 원격 import, 소스 파일의 적절한 포맷 적용 같은 특수 컨셉에 대한 공유된 이해를 형성하는데 필요한 최소한의 것들만을 할 수 있고, 따라서 함께 동작하는 패키지와 도구들을 만드는걸 가능하게 하는데, 이것들 모두가 핵심적인 세부사항에 대해 모두 합의하고 있기 때문입니다.

이 아이디어에 대해선 잠시 후 다시 이야기 하겠습니다.

### Why is Go open source?

하지만 먼저, 앞서 이야기 했듯, 덜 하고 더 가능하게 하라의 균형이 더 넓은 Go 오픈소스 프로젝트에의 우리의 작업을 가이드 하는지 설명하고자 합니다. 그러기 위해선, 왜 Go 가 오픈소스가 되었는지를 이야기해야겠죠.

구글은 저와 다른 사람들에게 Go 를 위해 일하라고 돈을 주는데, 왜냐하면, 구글의 프로그래머들이 더 생산적이 되면, 구글은 제품을 더 빨리 만들고, 그것들을 더 쉽게 관리하고, 그럴 수 있기 때문입니다. 하지만 왜 Go 를 오픈소스로 했을까요? 왜 구글은 이 이익을 세계와 공유해야 했을까요?

물론, 우리 중 많은 사람들이 Go 전에도 오픈소스 프로젝트에 참여했고, 우린 자연스럽게 Go 가 이 오픈소스 세계의 일부가 되길 바랬습니다. 하지만 우리의 선호도가 사업적 정당성은 아닙니다. 이 사업적 정당성은 Go 가 오픈소스가 되는게 Go 가 성공할 수 있는 유일한 방법이었다는 것입니다. 구글에서 Go 를 만든 우리 팀은 이걸 첫날부터 알았습니다. 우린 Go 가 성공하기 위해선 가능한 많은 사람들에게 사용될 수 있어야 한다는 것을 알았습니다.

폐쇄된 언어는 죽습니다.

언어는 크고 넓은 커뮤니티를 필요로 합니다.

언어는 여러분이 특정 도구나 라이브러리가 필요할 때 그게 이미 그 주제를 여러분보다 잘 아는, 그리고 그걸 훌륭하게 만들기 위해 여러분보다 많은 시간을 쏟은 다른 누군가에 의해 만들어져 있게끔 많은 소프트웨어를 만드는 많은 사람을 필요로 합니다.

언어는 문제가 빠르게 정의되고 고쳐질 수 있게끔 버그를 보고하는 많은 사람을 필요로 합니다. Plan 9 C 컴파일러에 비해서 Go 컴파일러는 훨씬 사용자가 많기 때문에 훨씬 안정적이고 표준을 더 잘 따릅니다.

언어는 한가지 사용처에만 과하게 적합해서 기술 환경이 변할 때 쓸모없지 않게끔 많은 다른 목적들로 사용하는 많은 사용자를 필요로 합니다.

언어는 그에 대한 책을 쓰거나 수업이나 이 컨퍼런스와 같은 컨퍼런스들을 여는 시장이 존재할 수 있게끔, 그걸 배우고자 하는 많은 사람을 필요로 합니다.

이 중 어떤 것도 Go 가 구글 내에만 있었다면 이뤄질 수 없었습니다. Go 는 구글 또는 어떤 회사나 폐쇄된 환경에서 질식사 했을 겁니다.

기본적으로, Go 는 공개되어야 하고, Go 는 여러분을 필요로 합니다. Go 는 여러분 모두가 없었다면, 전세계에서 모든 다른 종류의 프로젝트에 Go 를 사용하는 모든 사람이 없었다면 성공하지 못했을 겁니다.

결국, 구글의 Go 팀은 모든 Go 커뮤니티에 대한 지원을 할 수 있을 만큼 커지지도 못했을 겁니다. 확장을 유지하기 위해, 우린 덜 하면서 이 모든걸 ``더'' 가능하게 해야 합니다. 오픈소스는 그 큰 부분입니다.

### Go's open source

What does open source mean? The minimum requirement is to open the source code, making it available under an open source license, and we've done that.

But we also opened our development process: since announcing Go, we've done all our development in public, on public mailing lists open to all. We accept and review source code contributions from anyone. The process is the same whether you work for Google or not. We maintain our bug tracker in public, we discuss and develop proposals for changes in public, and we work toward releases in public. The public source tree is the authoritative copy. Changes happen there first. They are only brought into Google's internal source tree later. For Go, being open source means that this is a collective effort that extends beyond Google, open to all.

Any open source project starts with a few people, often just one, but with Go it was three: Robert Griesemer, Rob Pike, and Ken Thompson. They had a vision of what they wanted Go to be, what they thought Go could do better than existing languages, and Robert will talk more about that tomorrow morning. I was the next person to join the team, and then Ian Taylor, and then, one by one, we've ended up where we are today, with hundreds of contributors.

Thank You to the many people who have contributed code or ideas or bug reports to the Go project so far. We tried to list everyone we could in our space in the program today. If your name is not there, I apologize, but thank you.

I believe the hundreds of contributors so far are working toward a shared vision of what Go can be. It's hard to put words to these things, but I did my best to explain one part of the vision earlier: Do Less, Enable More.

### Google's role

A natural question is: What is the role of the Go team at Google, compared to other contributors? I believe that role has changed over time, and it continues to change. The general trend is that over time the Go team at Google should be doing less and enabling more.

In the very early days, before Go was known to the public, the Go team at Google was obviously working by itself. We wrote the first draft of everything: the specification, the compiler, the runtime, the standard library.

Once Go was open sourced, though, our role began to change. The most important thing we needed to do was communicate our vision for Go. That's difficult, and we're still working at it.. The initial implementation was an important way to communicate that vision, as was the development work we led that resulted in Go 1, and the various blog posts, and articles, and talks we've published.

But as Rob said at Gophercon last year, "the language is done." Now we need to see how it works, to see how people use it, to see what people build. The focus now is on expanding the kind of work that Go can help with.

Google's primarily role is now to enable the community, to coordinate, to make sure changes work well together, and to keep Go true to the original vision.

Google's primary role is: Do Less. Enable More.

I mentioned earlier that we'd rather have a small number of features that enable, say, 90% of the target use cases, and avoid the orders of magnitude more features necessary to reach 99 or 100%. We've been successful in applying that strategy to the areas of software that we know well. But if Go is to become useful in many new domains, we need experts in those areas to bring their expertise to our discussions, so that together we can design small adjustments that enable many new applications for Go.

This shift applies not just to design but also to development. The role of the Go team at Google continues to shift more to one of guidance and less of pure development. I certainly spend much more time doing code reviews than writing code, more time processing bug reports than filing bug reports myself. We need to do less and enable more.

As design and development shift to the broader Go community, one of the most important things we the original authors of Go can offer is consistency of vision, to help keep Go Go. The balance that we must strike is certainly subjective. For example, a mechanism for extensible syntax would be a way to enable more ways to write Go code, but that would run counter to our goal of having a consistent language without different dialects.

We have to say no sometimes, perhaps more than in other language communities, but when we do, we aim to do so constructively and respectfully, to take that as an opportunity to clarify the vision for Go.

Of course, it's not all coordination and vision. Google still funds Go development work. Rick Hudson is going to talk later today about his work on reducing garbage collector latency, and Hana Kim is going to talk tomorrow about her work on bringing Go to mobile devices. But I want to make clear that, as much as possible, we aim to treat development funded by Google as equal to development funded by other companies or contributed by individuals using their spare time. We do this because we don't know where the next great idea will come from. Everyone contributing to Go should have the opportunity to be heard.

### Examples

I want to share some evidence for this claim that, over time, the original Go team at Google is focusing more on coordination than direct development.

First, the sources of funding for Go development are expanding. Before the open source release, obviously Google paid for all Go development. After the open source release, many individuals started contributing their time, and we've slowly but steadily been growing the number of contributors supported by other companies to work on Go at least part-time, especially as it relates to making Go more useful for those companies. Today, that list includes Canonical, Dropbox, Intel, Oracle, and others. And of course Gophercon and the other regional Go conferences are organized entirely by people outside Google, and they have many corporate sponsors besides Google.

Second, the conceptual depth of Go development done outside the original team is expanding.

Immediately after the open source release, one of the first large contributions was the port to Microsoft Windows, started by Hector Chu and completed by Alex Brainman and others. More contributors ported Go to other operating systems. Even more contributors rewrote most of our numeric code to be faster or more precise or both. These were all important contributions, and very much appreciated, but for the most part they did not involve new designs.

More recently, a group of contributors led by Aram Hăvărneanu ported Go to the ARM 64 architecture, This was the first architecture port by contributors outside Google. This is significant, because in general support for a new architecture requires more design work than support for a new operating system. There is more variation between architectures than between operating systems.

Another example is the introduction over the past few releases of preliminary support for building Go programs using shared libraries. This feature is important for many Linux distributions but not as important for Google, because we deploy static binaries. We have been helping guide the overall strategy, but most of the design and nearly all of the implementation has been done by contributors outside Google, especially Michael Hudson-Doyle.

My last example is the go command's approach to vendoring. I define vendoring as copying source code for external dependencies into your tree to make sure that they doesn't disappear or change underfoot.

Vendoring is not a problem Google suffers, at least not the way the rest of the world does. We copy open source libraries we want to use into our shared source tree, record what version we copied, and only update the copy when there is a need to do so. We have a rule that there can only be one version of a particular library in the source tree, and it's the job of whoever wants to upgrade that library to make sure it keeps working as expected by the Google code that depends on it. None of this happens often. This is the lazy approach to vendoring.

In contrast, most projects outside Google take a more eager approach, importing and updating code using automated tools and making sure that they are always using the latest versions.

Because Google has relatively little experience with this vendoring problem, we left it to users outside Google to develop solutions. Over the past five years, people have built a series of tools. The main ones in use today are Keith Rarick's godep, Owen Ou's nut, and the gb-vendor plugin for Dave Cheney's gb,

There are two problems with the current situation. The first is that these tools are not compatible out of the box with the go command's "go get". The second is that the tools are not even compatible with each other. Both of these problems fragment the developer community by tool.

Last fall, we started a public design discussion to try to build consensus on some basics about how these tools all operate, so that they can work alongside "go get" and each other.

Our basic proposal was that all tools agree on the approach of rewriting import paths during vendoring, to fit with "go get"'s model, and also that all tools agree on a file format describing the source and version of the copied code, so that the different vendoring tools can be used together even by a single project. If you use one today, you should still be able to use another tomorrow.

Finding common ground in this way was very much in the spirit of Do Less, Enable More. If we could build consensus about these basic semantic aspects, that would enable "go get" and all these tools to interoperate, and it would enable switching between tools, the same way that agreement about how Go programs are stored in text files enables the Go compiler and all text editors to interoperate. So we sent out our proposal for common ground.

Two things happened.

First, Daniel Theophanes started a vendor-spec project on GitHub with a new proposal and took over coordination and design of the spec for vendoring metadata.

Second, the community spoke with essentially one voice to say that rewriting import paths during vendoring was not tenable. Vendoring works much more smoothly if code can be copied without changes.

Keith Rarick posted an alternate proposal for a minimal change to the go command to support vendoring without rewriting import paths. Keith's proposal was configuration-free and fit in well with the rest of the go command's approach. That proposal will ship as an experimental feature in Go 1.5 and likely enabled by default in Go 1.6. And I believe that the various vendoring tool authors have agreed to adopt Daniel's spec once it is finalized.

The result is that at the next Gophercon we should have broad interoperability between vendoring tools and the go command, and the design to make that happen was done entirely by contributors outside the original Go team.

Not only that, the Go team's proposal for how to do this was essentially completely wrong. The Go community told us that very clearly. We took that advice, and now there's a plan for vendoring support that I believe everyone involved is happy with.

This is also a good example of our general approach to design. We try not to make any changes to Go until we feel there is broad consensus on a well-understood solution. For vendoring, feedback and design from the Go community was critical to reaching that point.

This general trend toward both code and design coming from the broader Go community is important for Go. You, the broader Go community, know what is working and what is not in the environments where you use Go. We at Google don't. More and more, we will rely on your expertise, and we will try to help you develop designs and code that extend Go to be useful in more settings and fit well with Go's original vision. At the same time, we will continue to wait for broad consensus on well-understood solutions.

This brings me to my last point.

### Code of Conduct

I've argued that Go must be open, and that Go needs your help.

But in fact Go needs everyone's help. And everyone isn't here.

Go needs ideas from as many people as possible.

To make that a reality, the Go community needs to be as inclusive, welcoming, helpful, and respectful as possible.

The Go community is large enough now that, instead of assuming that everyone involved knows what is expected, I and others believe that it makes sense to write down those expectations explicitly. Much like the Go spec sets expectations for all Go compilers, we can write a spec setting expectations for our behavior in online discussions and in offline meetings like this one.

Like any good spec, it must be general enough to allow many implementations but specific enough that it can identify important problems. When our behavior doesn't meet the spec, people can point that out to us, and we can fix the problem. At the same time, it's important to understand that this kind of spec cannot be as precise as a language spec. We must start with the assumption that we will all be reasonable in applying it.

This kind of spec is often referred to as a Code of Conduct. Gophercon has one, which we've all agreed to follow by being here, but the Go community does not. I and others believe the Go community needs a Code of Conduct.

But what should it say?

I believe the most important overall statement we can make is that if you want to use or discuss Go, then you are welcome here, in our community. That is the standard I believe we aspire to.

If for no other reason (and, to be clear, there are excellent other reasons), Go needs as large a community as possible. To the extent that behavior limits the size of the community, it holds Go back. And behavior can easily limit the size of the community.

The tech community in general and the Go community in particular is skewed toward people who communicate bluntly. I don't believe this is fundamental. I don't believe this is necessary. But it's especially easy to do in online discussions like email and IRC, where plain text is not supplemented by the other cues and signals we have in face-to-face interactions.

For example, I have learned that when I am pressed for time I tend to write fewer words, with the end result that my emails seem not just hurried but blunt, impatient, even dismissive. That's not how I feel, but it's how I can come across, and that impression can be enough to make people think twice about using or contributing to Go. I realized I was doing this when some Go contributors sent me private email to let me know. Now, when I am pressed for time, I pay extra attention to what I'm writing, and I often write more than I naturally would, to make sure I'm sending the message I intend.

I believe that correcting the parts of our everyday interactions, intended or not, that drive away potential users and contributors is one of the most important things we can all do to make sure the Go community continues to grow. A good Code of Conduct can help us do that.

We have no experience writing a Code of Conduct, so we have been reading existing ones, and we will probably adopt an existing one, perhaps with minor adjustments. The one I like the most is the Django Code of Conduct, which originated with another project called SpeakUp! It is structured as an elaboration of a list of reminders for everyday interaction.

"Be friendly and patient. Be welcoming. Be considerate. Be respectful. Be careful in the words that you choose. When we disagree, try to understand why."

I believe this captures the tone we want to set, the message we want to send, the environment we want to create for new contributors. I certainly want to be friendly, patient, welcoming, considerate, and respectful. I won't get it exactly right all the time, and I would welcome a helpful note if I'm not living up to that. I believe most of us feel the same way.

I haven't mentioned active exclusion based on or disproportionately affecting race, gender, disability, or other personal characteristics, and I haven't mentioned harassment. For me, it follows from what I just said that exclusionary behavior or explicit harassment is absolutely unacceptable, online and offline. Every Code of Conduct says this explicitly, and I expect that ours will too. But I believe the SpeakUp! reminders about everyday interactions are an equally important statement. I believe that setting a high standard for those everyday interactions makes extreme behavior that much clearer and easier to deal with.

I have no doubts that the Go community can be one of the most friendly, welcoming, considerate, and respectful communities in the tech industry. We can make that happen, and it will be a benefit and credit to us all.

Andrew Gerrand has been leading the effort to adopt an appropriate Code of Conduct for the Go community. If you have suggestions, or concerns, or experience with Codes of Conduct, or want to be involved, please find Andrew or me during the conference. If you'll still be here on Friday, Andrew and I are going to block off some time for Code of Conduct discussions during Hack Day.

Again, we don't know where the next great idea will come from. We need all the help we can get. We need a large, diverse Go community.

### Thank You

I consider the many people releasing software for download using “go get,” sharing their insights via blog posts, or helping others on the mailing lists or IRC to be part of this broad open source effort, part of the Go community. Everyone here today is also part of that community.

Thank you in advance to the presenters who over the next few days will take time to share their experiences using and extending Go.

Thank you in advance to all of you in the audience for taking the time to be here, to ask questions, and to let us know how Go is working for you. When you go back home, please continue to share what you've learned. Even if you don't use Go for daily work, we'd love to see what's working for Go adopted in other contexts, just as we're always looking for good ideas to bring back into Go.

Thank you all again for making the effort to be here and for being part of the Go community.

For the next few days, please: tell us what we're doing right, tell us what we're doing wrong, and help us all work together to make Go even better.

Remember to be friendly, patient, welcoming, considerate, and respectful.

Above all, enjoy the conference.

By Russ Cox
