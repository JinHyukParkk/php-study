# 5.2 백도어 URL
 백도어 URL은 URL을 통한 직접 액세스를 의도하지 않았는데 URL을 통해서 직접 리소스에 액세스할 수 있는 것을 말합니다. 예를 들면 인증된 사용자에게 민감한 정보를 제공하는 웹 응용프로그램이 있다고 할때
 ```
 <?php
    $authenticated = FALSE;
    $authenticated = check_auth();
    /* ... */
    if($authenticated) {
        include './sensitive.php';
    }
 ?>
 ```
 웹 서버 루트 밑에 있는 모든 리소스는 그에 해당하는 URL을 갖습니다. 마찬가지로 위의 sensitive.php는 웹 서버 루트 밑에 있기 때문에 브라우저에서 의도한 액세스 컨트롤을 우회해서 직접 액세스할 수 있습니다. 때에 따라 이렇게 노출된 스트립트는 위험도가 높아질 수도 있습니다.

 위의 백도어 URL 공격을 막기위해서 역시 앞 장의 소스 코드 유출의 해결법과 같이 웹 서버 루트 바깥에 include 파일들을 저장해두어야 합니다. 웹 서버 루트안에 저장할 수 있는 것은 노출되어도 되는, URL 통해서 접근 가능한 파일뿐입니다.