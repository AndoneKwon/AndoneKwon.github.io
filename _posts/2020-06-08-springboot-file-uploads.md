---
layout: post
title: "Spring boot File upload"
date: 2020-04-06
excerpt: "스프링부트 파일업로드"
spring_boot: true
comments: true
tag: [timezone에러]
---
# Spring boot File upload

최근 중고플랫폼 프로젝트를 하며 중고 거래에 핵심은 사진파일 업로드이기 때문에 파일업로드를 구현하기로 하였다.

이전에 node.js로 프로젝트를 할 때 파일업로드를 구현한 경험이 있지만..역시나 스프링은 나에겐 복잡..하다.

아무튼.. 내가 여러가지로 조금 고생한 내용들을 누군가 참고하길 바라며..

우선 테스트용 view로 mustache로 하기 때문에(실제로는 React를 이용하여 front end를 구현한다.) view를 먼저 보도록 한다.

    <form action="/posts/uploadMultipleFiles" method="post" enctype="multipart/form-data">
    <div>
        <input multiple="multiple" type="file" name="files"/>
    </div>

    <div>
        <button class="btn indigo waves-effect waves-light"
                type="submit" name="save">

            Submit<i class="mdi-content-send right"></i>
        </button>
    </div>
    </form>

아주 간단하다.     

    <form action="/posts/uploadMultipleFiles" method="post" enctype="multipart/form-data">

이 부분에서 action은 spring cotroller에서 Request가 mapping되는 부분이다. 기본적으로 multifile upload는 Post방식으로만 가능하다. enctype도 multipart/form-data로 지정해 주도록 한다.

자, 뷰는 대충 됐다.

    @RequestMapping("/uploadMultipleFiles")
    public String fileupload(HttpServletRequest request, @RequestBody List<MultipartFile> files){
        try{
            for(int i=0;i<files.size();i++){
                files.get(i).transferTo(new File("파일경로"+files.get(i).getOriginalFilename()));
            }
        }catch (IllegalStateException | IOException e){
            e.printStackTrace();
        }
        return "file upload";
    }

Spring에서 컨트롤러 부분이다. DTO와 Service로 사실 나눠야 하지만, 게시판에서 파일 업로드를 할거이기 때문에 그것은 다음으로 넘기도록 한다. List로 받아서 반복해준다.(이거 같은 경우에는 이게 맞는 방법인지 잘 모르겠..다. 다음에 고쳐봐야지.)

기본적으로 파일의 용량제한, 파일의 확장자 등은 front-end단에서 검사해준다는 가정하에 코드를 작성한다.

Body에 파일 정보들을 받아서 List로 저장해준다.

그 후 그것을 files로 이름을 만들어 주고 그걸 transferTo(New File("파일경로"))로 파일을 만들어주고 저장하고자 하는 경로로 넣어준다.

자, 여기까지만 하면 기본적으로 멀티 파일업로드는 완성된거라 보면 된다.

근데 만약 여러 파일을 업로드 하면..

    multipart.MaxUploadSizeExceededException: Maximum upload size exceeded ...

이런 에러가 발생할 것이다. 별 문제는 아니고 톰켓에서 기본 업로드 파일 제한 용량을 1MB로 자동설정 해서 생기는 문제이다.

gradle을 이용해 빌드할 경우 application.properties에서 아래와 같이 설정해주면 된다.(Spring boot 2.3.0 버전 기준이다.)

    spring.servlet.multipart.max-request-size=1000MB
    spring.servlet.multipart.max-file-size=1000MB

최대 용량을 적당하게 늘려주고 실행하면 업로드가 잘 되는 모습을 볼 수 있다.

<hr>

https://m.blog.naver.com/PostView.nhn?blogId=poem1979&logNo=221663648794&proxyReferer=https:%2F%2Fwww.google.com%2F

이분 예시를 보고 구현하였다.