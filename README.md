const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

console.log("مرحبا! كيف يمكنني مساعدتك؟");

rl.setPrompt('أنت: ');
rl.prompt();

rl.on('line', (input) => {
  if (input.trim().toLowerCase() === "مرحبا") {
    console.log("أنا: مرحبا! كيف يمكنني مساعدتك؟");
  } else if (input.trim().toLowerCase() === "شكرا") {
    console.log("أنا: على الرحب والسعة!");
  } else {
    console.log("أنا: آسف، لم أفهم ما تقصد.");
  }
  rl.prompt();
});
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

console.log("مرحبا! يمكنك طلب معلومات عن:");
console.log("1. التاريخ");
console.log("2. الجغرافيا");
console.log("3. العلوم");
console.log("4. الثقافة");

const getInfo = () => {
  rl.question('اختر رقم الخيار: ', (choice) => {
    switch (choice) {
      case '1':
        console.log("التاريخ:");
        console.log("الحرب العالمية الأولى: 1914-1918");
        console.log("الحرب العالمية الثانية: 1939-1945");
        break;
      case '2':
        console.log("الجغرافيا:");
        console.log("أكبر قارة: آسيا");
        console.log("أكبر محيط: المحيط الهادئ");
        break;
      case '3':
        console.log("العلوم:");
        console.log("أسرع حيوان: الفهد");
        console.log("أكبر كوكب: المشتري");
        break;
      case '4':
        console.log("الثقافة:");
        console.log("أشهر كتاب: ألف ليلة وليلة");
        console.log("أشهر فنان: ليوناردو دافنشي");
        break;
      default:
        console.log("اختيار غير صالح");
    }
    rl.question('هل تريد الاستمرار؟ (نعم/لا): ', (response) => {
      if (response.toLowerCase() === 'لا') {
        rl.close();
      } else {
        getInfo();
      }
    });
  });
};

getInfo();
const axios = require('axios');

const createFacebookGroup = async (groupName, groupDescription, accessToken) => {
  try {
    const response = await axios.post(`https:                                     
      name: groupName,
      description: groupDescription,
      access_token: accessToken
    });
    console.log(`//graph.facebook.com/v13.0/groups`, {
      name: groupName,
      description: groupDescription,
      access_token: accessToken
    });
    console.log(`تم إنشاء المجموعة بنجاح: ${response.data.id}`);
    return response.data.id;
  } catch (error) {
    console.error(`خطأ في إنشاء المجموعة: ${error.message}`);
  }
};

const addMemberToGroup = async (groupId, userId, accessToken) => {
  try {
    const response = await axios.post(`https://graph.facebook.com/v13.0/${groupId}/members`, {
      user: userId,
      access_token: accessToken
    });
    console.log(`تم إضافة العضو بنجاح`);
  } catch (error) {
    console.error(`خطأ في إضافة العضو: ${error.message}`);
  }
};

// استخدم الدوال لإنشاء مجموعة وإضافة أعضاء
const groupName = 'مجموعة الدردشة';
const groupDescription = 'مجموعة للدردشة والمناقشة';
const accessToken = 'YOUR_ACCESS_TOKEN';
const groupId = await createFacebookGroup(groupName, groupDescription, accessToken);
const userId = 'USER_ID_TO_ADD';
addMemberToGroup(groupId, userId, accessToken);

