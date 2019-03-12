# Codeigniter를 이용한 Restful API 개발

## 개발환경 셋팅
이슈 1 - Windows 환경에서 Dockerfile 오류 발생 - 수정
이슈 2 - Windows 환경에서 DB Connect 이슈 발생 - Docker --> 로컬환경 셋팅으로 변경하여 처리함 

## Create Database
DROP DATABASE IF EXISTS `idus`;
CREATE DATABASE IF NOT EXISTS `idus`;
USE `idus`;

## Create User

create user 'idus'@'localhost' identified by 'idus';

grant all privileges on *.* to 'idus'@'localhost';

create user 'idus'@'%' identified by 'idus';

grant all privileges on *.* to 'idus'@'%';

# Create Table member_lsit
DROP TABLE IF EXISTS `member_list`;
CREATE TABLE IF NOT EXISTS `member_list` (
  `idx` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `email` varchar(50) NOT NULL DEFAULT '',
  `password` varchar(64) NOT NULL DEFAULT '',
  `regdate` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `name` varchar(50) NOT NULL DEFAULT '',
  `affiliate` varchar(50) DEFAULT NULL,
  `phone` varchar(13) NOT NULL,
  `eventagree` tinyint(1) unsigned zerofill NOT NULL DEFAULT '0',
  PRIMARY KEY (`idx`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

# Insert member_list
INSERT INTO `idus`.`member_list` (`email`, `password`, `regdate`, `name`, `affiliate`, `phone`) VALUES
('idus@idus.com', '122345', '2019-01-18 11:55:37', 'idusdev', 'idus@idus.com', '01012345678');


# API 목록

## 회원 데이터 생성(회원가입) API
POST
http://localhost/index.php/api/idus/users

## 회원 데이터 수정 API
PUT
http://localhost/index.php/api/idus/users/idx/3


## 회원 데이터 삭제 API
DELETE
http://localhost/index.php/api/idus/users/idx/2

## 하나의 회원 데이터 출력 API
GET
http://localhost/index.php/api/idus/users/id/1

## 여러 회원 데이터 출력(페이지를 나눠 출력) API
GET
http://localhost/index.php/api/idus/users