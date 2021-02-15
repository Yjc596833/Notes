<!--
 * @Author: your name
 * @Date: 2021-01-21 10:24:09
 * @LastEditTime: 2021-01-21 10:24:36
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Mysql\Json处理.md
-->
SELECT   * FROM yejiancongtest.web_account_info where JSON_CONTAINS(officialCert,JSON_Array(6));