# Error codes

Every refusal is `application/problem+json` (RFC 9457). The `code` is a function of
the refusal reason alone: the same reason always gives the same code, status, and
reason text, in the caller's own Interface language.

| Code | HTTP | English reason | Arabic reason |
|---|---|---|---|
| `authentication_failed` | 401 | Authentication failed: the request carries no valid session or Personal Access Token. | فشلت المصادقة: لا يحمل الطلب جلسة صالحة ولا رمز وصول شخصيًا صالحًا. |
| `access_denied` | 403 | Access is denied: you are not permitted to perform this action. | تم رفض الوصول: لا يُسمح لك بتنفيذ هذا الإجراء. |
| `purpose_required` | 403 | Access is denied: select one of the two access purposes and, where required, identify the matter of the investigation. | تم رفض الوصول: اختر أحد غرضَي الوصول، وحدِّد موضوع التحقيق عندما يكون ذلك مطلوبًا. |
| `invalid_field` | 422 | One or more fields are invalid. Each listed field states the rule it breaks and the allowed limit. | حقل واحد أو أكثر غير صالح. يبيّن كل حقل مُدرَج القاعدة التي يخالفها والحدّ المسموح به. |
| `upload_too_large` | 413 | The upload is rejected because the files of the Submission would exceed the Maximum Submission Size in bytes. | رُفض الرفع لأن ملفات الإرسال ستتجاوز الحجم الأقصى للإرسال بالبايت. |
| `upload_incomplete` | 409 | The upload cannot be finished because each listed file is not fully received or is corrupt. | لا يمكن إنهاء الرفع لأن كل ملف مُدرَج لم يُستلَم كاملًا أو تالف. |
| `run_status_conflict` | 409 | This action is not possible in the current Run Status of the Evaluation Run. | لا يمكن تنفيذ هذا الإجراء في الحالة الحالية لعملية التقييم. |
| `load_check_required` | 409 | A successful Load Check of the current Declaration version is required before the Evaluation Run can be confirmed. | يلزم فحص تحميل ناجح للنسخة الحالية من التصريح قبل تأكيد عملية التقييم. |
| `no_pricing_tier` | 409 | No Pricing Tier applies to this Submission because no Parameter Count was reported or it lies outside every configured range. | لا تنطبق أي فئة تسعير على هذا الإرسال لأنه لم يُبلَّغ عن عدد المعاملات أو لأنه يقع خارج جميع النطاقات المُعدَّة. |
| `quota_exhausted` | 409 | The Free Run Quota of the current period is used up. It renews on the stated date, and the run can be confirmed now at the stated Paid Tier price. | نفدت حصة عمليات التقييم المجانية للفترة الحالية. تتجدد الحصة في التاريخ المذكور، ويمكن تأكيد عملية التقييم الآن بسعر الفئة المدفوعة المذكور. |
| `payment_failed` | 402 | The payment failed for the stated reason. The Evaluation Run is still awaiting confirmation and can be confirmed again at the displayed price. | فشل الدفع للسبب المذكور. لا تزال عملية التقييم بانتظار التأكيد، ويمكن تأكيدها مجددًا بالسعر المعروض. |
| `payment_method_required` | 402 | No saved payment method is available. Add one in the web interface at the stated address. | لا توجد وسيلة دفع محفوظة. أضف وسيلة دفع في واجهة الويب على العنوان المذكور. |
| `files_deleted` | 410 | The Weights and Declaration of this Submission are deleted and must be uploaded again. | حُذفت الأوزان والتصريح الخاصان بهذا الإرسال، ويجب رفعهما من جديد. |
| `no_season_in_progress` | 409 | No Season is in progress, so no Evaluation Run can be created. | لا يوجد موسم جارٍ، لذلك لا يمكن إنشاء عملية تقييم. |
| `results_immutable` | 409 | Recorded results are final and cannot be entered, changed, replaced, or removed. | النتائج المسجَّلة نهائية، ولا يمكن إدخالها أو تغييرها أو استبدالها أو إزالتها. |
| `duplicate_leaderboard_entry` | 409 | This Model Fingerprint already has the stated Leaderboard entry in the same Season and Track. | لبصمة النموذج هذه إدخال قائم في لوحة الصدارة ضمن الموسم والمسار نفسيهما، وهو الإدخال المذكور. |
| `report_pending` | 409 | The Report is pending and cannot be published yet. | التقرير معلَّق ولا يمكن نشره بعد. |
| `defect_rerun_exists` | 409 | A Defect re-run has already been requested under this Defect Notice. The existing re-run and its Run Status are stated. | سبق طلب إعادة تقييم بسبب خلل بموجب إشعار الخلل هذا. وتُذكَر إعادة التقييم القائمة وحالتها. |
| `defect_notice_required` | 409 | A Defect re-run requires a Defect Notice on the Evaluation Run. | تتطلب إعادة التقييم بسبب خلل وجود إشعار خلل على عملية التقييم. |
| `defect_notice_exists` | 409 | This Evaluation Run already has a Defect Notice attached. The existing Defect Notice and its confirmation date are stated. | تحمل عملية التقييم هذه إشعار خلل مُرفقًا مسبقًا. ويُذكَر إشعار الخلل القائم وتاريخ تأكيده. |
| `invalid_link` | 422 | The checkpoint link is refused because the stated condition is violated. | رُفض ربط نقطة الحفظ لأن الشرط المذكور غير مستوفًى. |
| `task_set_invalid` | 422 | The Task Set Definition is invalid. Every violation is listed with its line number. | تعريف مجموعة المهام غير صالح. تُدرَج كل مخالفة مع رقم سطرها. |
| `task_set_version_immutable` | 409 | A published Task Set Version cannot be changed. A change requires a new Task Set Version. | لا يمكن تغيير نسخة منشورة من مجموعة المهام. ويتطلب أي تغيير نسخة جديدة من مجموعة المهام. |
| `licence_confirmation_required` | 422 | Confirmation that the licence permits showing the Items and Reference Answers to Model Owners is required. | يلزم تأكيد أن الترخيص يسمح بعرض العناصر والإجابات المرجعية على مالكي النماذج. |
| `season_invalid` | 422 | The Season cannot start because the listed settings are missing or mismatched. | لا يمكن بدء الموسم لأن الإعدادات المُدرَجة مفقودة أو غير متطابقة. |
| `season_setting_locked` | 409 | The settings of a started Season are fixed. A change requires a new Season. | إعدادات الموسم الذي بدأ ثابتة. ويتطلب أي تغيير موسمًا جديدًا. |
| `config_invalid` | 422 | The configuration change is rejected and every previous value is kept. Each rejected value is listed with the condition it violates. | رُفض تغيير التهيئة وبقيت جميع القيم السابقة. تُدرَج كل قيمة مرفوضة مع الشرط الذي تخالفه. |
| `judge_version_exists` | 409 | This Judge Version identifier is already registered, and a registered Judge Version cannot be changed. | معرِّف نسخة المُحكِّم هذا مسجَّل مسبقًا، ولا يمكن تغيير نسخة مُحكِّم مسجَّلة. |
| `review_action_unavailable` | 409 | The review action is not possible because the stated condition does not hold. | لا يمكن تنفيذ إجراء المراجعة لأن الشرط المذكور غير متحقق. |
| `reproduction_unavailable` | 409 | A verification re-run is not possible because each listed element is no longer retained or available. | لا يمكن إجراء إعادة التقييم للتحقق لأن كل عنصر مُدرَج لم يعد محفوظًا أو متاحًا. |
| `record_invalid` | 422 | The document does not conform to the Evaluation Record Format. Every violation is listed with its line number. | المستند لا يطابق صيغة سجل التقييم. تُدرَج كل مخالفة مع رقم سطرها. |
| `invalid_range` | 422 | The Parameter Count range is invalid because its lower bound is greater than its upper bound. | نطاق عدد المعاملات غير صالح لأن حدّه الأدنى أكبر من حدّه الأعلى. |
| `invalid_download_request` | 422 | The download request is invalid. Each invalid parameter is listed with its value. | طلب التنزيل غير صالح. يُدرَج كل وسيط غير صالح مع قيمته. |
| `hub_chat_rate_limited` | 429 | The Hub Chat rate limit is reached. You can send a message again from the stated time. | بلغتَ حدّ عدد رسائل محادثة المركز. يمكنك إرسال رسالة مجددًا ابتداءً من الوقت المذكور. |
| `hub_chat_unavailable` | 503 | The Hub Chat is unavailable right now. Your message was not counted; please try again later. | محادثة المركز غير متاحة حاليًا. لم تُحتسَب رسالتك؛ يُرجى المحاولة لاحقًا. |