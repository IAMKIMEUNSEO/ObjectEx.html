# ObjectEx.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h2> 1. new Object() 이용 사용자 객체 만들기 </h2>
    <script>
        {
            let account = new Object();     //사용자 객체 생성
            //속성 추가
            account.owner = 'Kim';     //계좌 소유자
            account.code = '123-456-78901';      //계좌번호
            account.balance = 15000;      //계좌 잔고
            //저축한 금액
            function inquiry() {
                return this.balance;
                //this.balance: 이(this) 객체 즉, account의 balance
                //this가 없으면 일반적인 함수의 전역 지역변수를 의미
            }
            account.inquiry = inquiry;
            //저축
            function deposit(money) {
                this.balance += money;
            }
            account.deposit = deposit;
            //인출
            function withdraw(money) {
                this.balance -= money;     //가정: money <= balance
                return money;     //인출금액 리턴
            }
            account.withdraw = withdraw;
            document.write('account.owner: ' + account.owner + '<br>');
            document.write('account.code: ' + account.code + '<br>');
            document.write('account.balance: ' + account.balance + '<br>');
            account.deposit(5000);
            document.write('account.balance(5000 저금): ' + account.balance + '<br>');
            account.withdraw(14000);
            document.write('account.balance(14000 인출): ' + account.balance + '<br>');
        }
    </script>
    <h2> 2. 리터럴 표기법을 이용하여 사용자 객체 만들기 </h2>
    <script>
        {
            let account = {
                //속성(Properties)
                owner: 'Kim',
                code: '123-456-78901',
                balance: 10000,
                //메소드(Method)
                inquiry: function () {
                    return this.balance;
                },
                deposit: function(money) {
                    this.balance += money;
                },
                withdraw: function(money) {
                    this.balance -= money;
                    return money;
                }
            }
            document.write('account.owner: ' + account.owner + '<br>');
            document.write('account.code: ' + account.code + '<br>');
            document.write('account.balance: ' + account.balance + '<br>');
            account.deposit(5000);
            document.write('account.balance(5000 저금): ' + account.balance + '<br>');
            account.withdraw(14000);
            document.write('account.balance(14000 인출): ' + account.balance + '<br>');
        }    
    </script>
</body>
</html>
