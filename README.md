# am-config-repo
CREATE SEQUENCE MANAGED_ASSET_SEQ ;
CREATE SEQUENCE ACCOUNT_SEQ ;
CREATE SEQUENCE ASSET_DETAIL_SEQ ;


CREATE TABLE account_detail(
   ACCOUNT_ID serial PRIMARY KEY,
   FIRST_NAME VARCHAR (50) NOT NULL,
   LAST_NAME VARCHAR (50) NOT NULL,
   EMAIL VARCHAR (50) NOT NULL,
   MOBILE VARCHAR (15) NOT NULL
);

CREATE TABLE ASSET_DETAIL(
   ASSET_DETAIL_ID serial PRIMARY KEY,
   DESCRIPTION VARCHAR (50) NOT NULL,
   ASSET_NUMBER VARCHAR (30) NOT NULL,
   SERIAL_NUMBER VARCHAR (30) NOT NULL,
   TAGGED_TO VARCHAR (50) NOT NULL,
   STATUS VARCHAR (15) NOT NULL
);


CREATE TABLE MANAGED_ASSET(
   MANAGED_ASSET_ID serial PRIMARY KEY,
   ASSET_ID serial,
   ACCOUNT_ID serial
);

alter table MANAGED_ASSET  add constraint fk_ASSET_ID foreign key (ASSET_ID) REFERENCES ASSET_DETAIL (ASSET_DETAIL_ID);
alter table MANAGED_ASSET  add constraint fk_ACCOUNT_ID foreign key (ACCOUNT_ID) REFERENCES account_detail (ACCOUNT_ID);

http://localhost:8080/am-account-details/accounts

{
	"firstName":"Prabhakaran",
	"lastName":"Ramaswamy",
	"email":"pramaswamy@gmail.com",
	"mobile":"9003100558"
}


http://localhost:8080/am-asset-details/assetdetails

{
	"description":"Laptop",
	"assetNumber":"1212",
	"serial":"123232",
	"taggedTo":"Prabhakaran Ramaswamy",
	"status":"tagged"
}